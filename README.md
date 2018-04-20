# 12345
#include <stdio.h>
#include<conio.h>
 int main() 
{
        int at[10],bt[10],temp[10];
        int i,j,small,count=0,time,t_process,total=0,counter=0,n,n1;
        double wt=0,tt=0,end;
        float awt,att;
        printf("\nEnter the Total Number of Processes:\t");
        scanf("%d",&t_process); 
        printf("\nEnter Details of %d Processes\n",t_process);
        for(i=0;i<t_process;i++)
         {
                printf("\nEnter Arrival Time:\t");
                scanf("%d",&at[i]);
                printf("Enter Burst Time:\t");
                scanf("%d",&bt[i]); 
                temp[i]=bt[i];
        }
          bt[9]=9999;  
         for(time=0;count!=t_process;time++)
         {
                   small=9;
                  for(i=0;i<t_process;i++)
                  {
                           if(at[i]<=time&&bt[i]<bt[small]&&bt[i]>0)
                        {
                                   small=i;
                        }
                  }
                  bt[small]--;
                  if(bt[small]==0)
                  {
                           count++;
                           end=time+1;
                           wt=wt+end-at[small]-temp[small];
                           tt=tt+end-at[small];
                  }
         }
        awt=wt/t_process; 
        att=tt/t_process;
         printf("\n\nAverage Waiting Time for SJF:\t%lf\n", awt);
            printf("Average Turnaround Time for SJF:\t%lf\n", att);
            printf("ROUND ROBIN SCHEDULING");
    int time_quantum,pid[10],need[10],waiting_time[10],turnaround_time[10];
int ct[10], flag[10],total_turnaround_time=0,total_waiting_time=0;
float average_waiting_time,average_turnaround_time;
printf("\t\t ROUND ROBIN SCHEDULING");
printf("\n\nEnter the number of Processors \n");
scanf("%d",&n);
n1=n;
printf("\n Enter the Time_Quantum \n");
scanf("%d",&time_quantum);
for(i=1;i<=n;i++)
{
printf("\n Enter the process ID %d arrival time ",i);
scanf("%d",&pid[i]);
printf("\n Enter the Burst Time of the process ");
scanf("%d",&ct[i]);
need[i]=ct[i];
}
for(i=1;i<=n;i++)
{
flag[i]=1;
waiting_time[i]=0;
}
while(n!=0)
{
for(i=1;i<=n;i++)
{
if(need[i]>=time_quantum)
{
for(j=1;j<=n;j++)
{
if((i!=j)&&(flag[i]==1)&&(need[j]!=0))
waiting_time[j]+=time_quantum;
}
need[i]-=time_quantum;
if(need[i]==0)
{
flag[i]=0;
n--;
}
}
else
{
for(j=1;j<=n;j++)
{
if((i!=j)&&(flag[i]==1)&&(need[j]!=0))
waiting_time[j]+=need[i];
}
need[i]=0;
n--;
flag[i]=0;
}
}
}
for(i=1;i<=n1;i++)
{
turnaround_time[i]=waiting_time[i]+ct[i];
total_waiting_time=total_waiting_time+waiting_time[i];
total_turnaround_time=total_turnaround_time+turnaround_time[i];
}
average_waiting_time=(float)total_waiting_time/n1;
average_turnaround_time=(float)total_turnaround_time/n1;
printf("\n\n Process \t Process ID \t BurstTime \t Waiting Time \t TurnaroundTime \n ");
for(i=1;i<=n1;i++)
{
printf("\n %5d \t %5d \t\t %5d \t\t %5d \t\t %5d \n", i,pid[i],ct[i],waiting_time[i],turnaround_time[i]);
}
printf("\n The average Waiting Time=%f",average_waiting_time);
printf("\n The average Turn around Time=%f",average_turnaround_time);
getch();          
}
