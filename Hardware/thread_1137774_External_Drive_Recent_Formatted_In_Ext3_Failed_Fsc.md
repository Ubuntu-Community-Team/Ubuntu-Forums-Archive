---
title: "External Drive Recent Formatted In Ext3 Failed Fsck:"
date: 2009-04-25
forum: Hardware
---

### Post by klepto on 2009-04-25
Yesterday I took a brand new WD My Book Studio Edition external hard drive
and formatted it to ext3 fs. I start backing up machines etc and then later I used Image For Linux and backed up my laptop on to the new external hard drive. 
After a reboot the drive couldn't be mounted and fsck gave these errors: 

> sudo fsck /dev/sdb1
[sudo] password for klepto:                               
fsck 1.41.3 
e2fsck 1.41.3 
fsck.ext3: Group descriptors look bad... trying backup blocks...
EXTERN1TB was not cleanly unmounted, check forced.              
Pass 1: Checking inodes, blocks, and sizes                      
Pass 2: Checking directory structure                            
Pass 3: Checking directory connectivity                         
Pass 4: Checking reference counts                               
Pass 5: Checking group summary information                      
Free blocks count wrong for group #324 (32254, counted=1791.  
Fix<y>? yes                                                     

Free blocks count wrong for group #325 (32254, counted=0).
Fix<y>? yes                                               

Free blocks count wrong for group #326 (32254, counted=0).
Fix<y>? yes                                               

Free blocks count wrong for group #327 (32254, counted=0).
Fix<y>? yes                                               

Free blocks count wrong for group #328 (32254, counted=0).
Fix<y>? yes                                               

Free blocks count wrong for group #329 (32254, counted=22224).
Fix<y>? yes                                                   

Free blocks count wrong for group #330 (32254, counted=19621).
Fix<y>? yes                                                   

Free blocks count wrong for group #331 (32254, counted=1791.
Fix<y>? yes                                                   

Free blocks count wrong for group #332 (32254, counted=320
Fix<y>? yes                                                  

Free blocks count wrong for group #333 (32254, counted=18442).
Fix<y>? yes                                                   

Free blocks count wrong for group #334 (32254, counted=22616).
Fix<y>? yes                                                   

Free blocks count wrong for group #335 (32254, counted=1791
Fix<y>? yes                                                   

Free blocks count wrong for group #336 (32254, counted=124).
Fix<y>? yes                                                 

Free blocks count wrong for group #608 (32254, counted=28156).
Fix<y>? yes                                                   

Free blocks count wrong for group #609 (32254, counted=6).
Fix<y>? yes                                               

Free blocks count wrong for group #610 (32254, counted=6).
Fix<y>? yes                                               

Free blocks count wrong for group #611 (32254, counted=6).
Fix<y>? yes                                               

Free blocks count wrong for group #612 (32254, counted=6232).
Fix<y>? yes                                                  

Free blocks count wrong for group #2657 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2658 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2659 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2660 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2661 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2662 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2663 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2664 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2665 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2666 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2667 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2668 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2669 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2670 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2671 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2672 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2673 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2674 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2675 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2676 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2677 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2678 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2679 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2680 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2681 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2682 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2683 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2684 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2685 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2686 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2687 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2688 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2689 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2690 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2691 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2692 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2693 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2694 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2695 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2696 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2697 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2698 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2699 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2700 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2701 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2702 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2703 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2704 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2705 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2706 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2707 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2708 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2709 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2710 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2711 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2712 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2713 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2714 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2715 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2716 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2717 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2718 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2719 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2720 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2721 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2722 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2723 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2724 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2725 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2726 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2727 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2728 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2729 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2730 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #2731 (32254, counted=12524).
Fix<y>? yes                                                    

Free blocks count wrong for group #4034 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4035 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4036 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4037 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4038 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4039 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4040 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4041 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4042 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4043 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4044 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4045 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4046 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4047 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4048 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4049 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4050 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4051 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4052 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4053 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4054 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4055 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4056 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4057 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4058 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #4059 (32254, counted=6155).
Fix<y>? yes                                                   

Free blocks count wrong for group #4060 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4061 (32254, counted=2).
Fix<y>? yes                                                

Free blocks count wrong for group #4062 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4063 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4064 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4065 (32254, counted=17984).
Fix<y>? yes                                                    

Free blocks count wrong for group #4066 (32254, counted=22203).
Fix<y>? yes                                                    

Free blocks count wrong for group #4067 (32254, counted=23170).
Fix<y>? yes                                                    

Free blocks count wrong for group #4068 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4069 (32254, counted=14320).
Fix<y>? yes                                                    

Free blocks count wrong for group #4070 (32254, counted=13032).
Fix<y>? yes                                                    

Free blocks count wrong for group #4071 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4072 (32254, counted=13540).
Fix<y>? yes                                                    

Free blocks count wrong for group #4073 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4074 (32254, counted=5).
Fix<y>? yes                                                

Free blocks count wrong for group #4075 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4076 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4077 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4078 (32254, counted=1283
Fix<y>? yes                                                    

Free blocks count wrong for group #4079 (32254, counted=10031).
Fix<y>? yes                                                    

Free blocks count wrong for group #4080 (32254, counted=16625).
Fix<y>? yes                                                    

Free blocks count wrong for group #4081 (32254, counted=17250).
Fix<y>? yes                                                    

Free blocks count wrong for group #4082 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4083 (32254, counted=19261).
Fix<y>? yes                                                    

Free blocks count wrong for group #4084 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4085 (32254, counted=4).
Fix<y>? yes                                                

Free blocks count wrong for group #4086 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4087 (32254, counted=8386).
Fix<y>? yes                                                   

Free blocks count wrong for group #4088 (32254, counted=15870).
Fix<y>? yes                                                    

Free blocks count wrong for group #4089 (32254, counted=3).
Fix<y>? yes                                                

Free blocks count wrong for group #4090 (32254, counted=6).
Fix<y>? yes                                                

Free blocks count wrong for group #4091 (32254, counted=182).
Fix<y>? yes                                                  

Free blocks count wrong for group #4092 (32254, counted=8947).
Fix<y>? yes                                                   

Free blocks count wrong for group #5152 (32254, counted=32251).
Fix<y>? yes                                                    

Free blocks count wrong for group #6404 (32254, counted=3583).
Fix<y>? yes                                                   

Free blocks count wrong for group #6405 (32254, counted=16390).
Fix<y>? yes                                                    

Free blocks count wrong for group #7216 (32254, counted=19966).
Fix<y>? yes                                                    

Free blocks count wrong for group #7217 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7218 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7219 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7220 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7221 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7222 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7223 (32254, counted=0).
Fix<y>? yes                                                

Free blocks count wrong for group #7224 (32254, counted=30035).
Fix<y>? yes                                                    

Free blocks count wrong (240306876, counted=235637310).
Fix<y>? yes                                            

yyyyyyyyyyyyFree inodes count wrong for group #324 (8192, counted=8141).
Fix<y>? yes                                                             

Directories count wrong for group #324 (0, counted=2).
Fix<y>? yes                                           

Free inodes count wrong for group #330 (8192, counted=8181).
Fix<y>? yes                                                 

Directories count wrong for group #330 (0, counted=1).
Fix<y>? yes                                           

Free inodes count wrong for group #331 (8192, counted=8157).
Fix<y>? yes                                                 

Directories count wrong for group #331 (0, counted=2).
Fix<y>? yes                                           

Free inodes count wrong for group #332 (8192, counted=815
Fix<y>? yes                                                 

Directories count wrong for group #332 (0, counted=1).
Fix<y>? yes                                           

Free inodes count wrong for group #333 (8192, counted=8163).
Fix<y>? yes                                                 

Directories count wrong for group #333 (0, counted=1).
Fix<y>? yes                                           

Free inodes count wrong for group #334 (8192, counted=8180).
Fix<y>? yes                                                 

Directories count wrong for group #334 (0, counted=1).
Fix<y>? yes                                           

Free inodes count wrong for group #335 (8192, counted=8177).
Fix<y>? yes                                                 

Directories count wrong for group #335 (0, counted=1).
Fix<y>? yes                                           

Free inodes count wrong for group #608 (8192, counted=8189).
Fix<y>? yes                                                 

Directories count wrong for group #608 (0, counted=2).
Fix<y>? yes                                           

Free inodes count wrong for group #2657 (8192, counted=8187).
Fix<y>? yes                                                  

Directories count wrong for group #2657 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4034 (8192, counted=8134).
Fix<y>? yes                                                  

Directories count wrong for group #4034 (0, counted=
Fix<y>? yes                                            

Free inodes count wrong for group #4037 (8192, counted=818
Fix<y>? yes                                                  

Directories count wrong for group #4037 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4040 (8192, counted=8187).
Fix<y>? yes                                                  

Directories count wrong for group #4040 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4045 (8192, counted=8187).
Fix<y>? yes                                                  

Directories count wrong for group #4045 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4046 (8192, counted=8161).
Fix<y>? yes                                                  

Directories count wrong for group #4046 (0, counted=12).
Fix<y>? yes                                             

Free inodes count wrong for group #4047 (8192, counted=8179).
Fix<y>? yes                                                  

Directories count wrong for group #4047 (0, counted=3).
Fix<y>? yes                                            

Free inodes count wrong for group #4048 (8192, counted=8183).
Fix<y>? yes                                                  

Directories count wrong for group #4048 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4051 (8192, counted=8180).
Fix<y>? yes                                                  

Directories count wrong for group #4051 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4053 (8192, counted=8189).
Fix<y>? yes                                                  

Directories count wrong for group #4053 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4057 (8192, counted=8181).
Fix<y>? yes                                                  

Directories count wrong for group #4057 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4058 (8192, counted=8163).
Fix<y>? yes                                                  

Directories count wrong for group #4058 (0, counted=9).
Fix<y>? yes                                            

Free inodes count wrong for group #4059 (8192, counted=8155).
Fix<y>? yes                                                  

Directories count wrong for group #4059 (0, counted=7).
Fix<y>? yes                                            

Free inodes count wrong for group #4060 (8192, counted=8186).
Fix<y>? yes                                                  

Directories count wrong for group #4060 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4065 (8192, counted=8186).
Fix<y>? yes                                                  

Directories count wrong for group #4065 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4066 (8192, counted=816
Fix<y>? yes                                                  

Directories count wrong for group #4066 (0, counted=5).
Fix<y>? yes                                            

Free inodes count wrong for group #4067 (8192, counted=8122).
Fix<y>? yes                                                  

Directories count wrong for group #4067 (0, counted=6).
Fix<y>? yes                                            

Free inodes count wrong for group #4068 (8192, counted=8126).
Fix<y>? yes                                                  

Directories count wrong for group #4068 (0, counted=8).
Fix<y>? yes                                            

Free inodes count wrong for group #4069 (8192, counted=8170).
Fix<y>? yes                                                  

Directories count wrong for group #4069 (0, counted=5).
Fix<y>? yes                                            

Free inodes count wrong for group #4071 (8192, counted=8184).
Fix<y>? yes                                                  

Directories count wrong for group #4071 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4073 (8192, counted=8165).
Fix<y>? yes                                                  

Directories count wrong for group #4073 (0, counted=
Fix<y>? yes                                            

Free inodes count wrong for group #4078 (8192, counted=8185).
Fix<y>? yes                                                  

Directories count wrong for group #4078 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4079 (8192, counted=8185).
Fix<y>? yes                                                  

Directories count wrong for group #4079 (0, counted=1).
Fix<y>? yes                                            

Free inodes count wrong for group #4081 (8192, counted=8181).
Fix<y>? yes                                                  

Directories count wrong for group #4081 (0, counted=4).
Fix<y>? yes                                            

Free inodes count wrong for group #4082 (8192, counted=8182).
Fix<y>? yes                                                  

Directories count wrong for group #4082 (0, counted=4).
Fix<y>? yes                                            

Free inodes count wrong for group #4083 (8192, counted=8181).
Fix<y>? yes                                                  

Directories count wrong for group #4083 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4084 (8192, counted=8185).
Fix<y>? yes                                                  

Directories count wrong for group #4084 (0, counted=2).
Fix<y>? yes                                            

Free inodes count wrong for group #4088 (8192, counted=8176).
Fix<y>? yes                                                  

Directories count wrong for group #4088 (0, counted=
Fix<y>? yes                                            

Free inodes count wrong for group #4092 (8192, counted=8177).
Fix<y>? yes                                                  

Directories count wrong for group #4092 (0, counted=4).
Fix<y>? yes                                            

Free inodes count wrong for group #5152 (8192, counted=8189).
Fix<y>? yes                                                  

Directories count wrong for group #5152 (0, counted=3).
Fix<y>? yes

Free inodes count wrong for group #6404 (8192, counted=8167).
Fix<y>? yes

Directories count wrong for group #6404 (0, counted=2).
Fix<y>? yes

Free inodes count wrong for group #6405 (8192, counted=8184).
Fix<y>? yes

Directories count wrong for group #6405 (0, counted=2).
Fix<y>? yes

Free inodes count wrong for group #7216 (8192, counted=8070).
Fix<y>? yes

Directories count wrong for group #7216 (0, counted=3).
Fix<y>? yes

Free inodes count wrong (61054965, counted=61054082).
Fix<y>? yes

y
EXTERN1TB: ***** FILE SYSTEM WAS MODIFIED *****
EXTERN1TB: 894/61054976 files (5.1% non-contiguous), 8552690/244190000 blocksMy question is should I suspect the files on the drive and just reformat it or did fsck fix the issue?

P.S. For some reason a bunch of smilies were in my paste. I tried to get rid of them

Thanks much

---

### Post by KhurramM on 2009-04-26
I would suggest u to go for a re-format if you can.

If it doesnt works try FAT32 format.

Hope this solves your issue.

---

