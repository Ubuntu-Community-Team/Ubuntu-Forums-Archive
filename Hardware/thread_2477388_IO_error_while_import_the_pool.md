---
title: "I/O error while import the pool"
date: 2022-07-23
forum: Hardware
---

### Post by chenqiusong on 2022-07-23
Hello everyone.
I have made a mistake on the zfs pool. I forgot transfer the cache SSD with the hard disk while I migrate the Pool.
The the corrupted like this


r```
oot@NasDell:~# zpool import -d /dev/disk/by-id/                                                            
   pool: CCCFile                                                                                            
     id: 948687002***4                                                                                 
  state: ONLINE                                                                                             
 action: The pool can be imported using its name or numeric identifier.                                     
 config:                                                                                                    
        CCCFile                            ONLINE                                                           
          mirror-0                         ONLINE                                                           
            wwn-0x50014ee6044e5c60         ONLINE                                                           
            wwn-0x50014ee2677bebb9         ONLINE                                                           
        cache                                                                                               
          nvme-eui.5cd2e4c80eb60100-part1                                                                   
        logs                                                                                                
          nvme-eui.5cd2e4c80eb60100-part2  ONLINE

```While I import it, the error message is :


```
root@NasDell:~# zpool import -d /dev/disk/by-id/ CCCFile                                                    
             cannot import 'CCCFile': I/O error                                                                          
        Destroy and re-create the pool from                                                                 
        a backup source. 

```Then I check the SSD state. All part is exist correctly.


```
root@NasDell:~# ls -l /dev/disk/by-id/*100*                                                                 
lrwxrwxrwx 1 root root 13 Jul 23 11:49 /dev/disk/by-id/nvme-eui.5cd2e4c80eb60100 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jul 23 11:49 /dev/disk/by-id/nvme-eui.5cd2e4c80eb60100-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jul 23 11:49 /dev/disk/by-id/nvme-eui.5cd2e4c80eb60100-part2 -> ../../nvme0n1p2

```

In my understanding, the reason is that the cache partition isn't marked as "ONLINE". So I try to change the sate. But it comes out no pools available.


```
root@NasDell:~# zpool online CCCFile nvme-eui.5cd2e4c80eb60100-part1                                        
cannot open 'CCCFile': no such pool 
root@NasDell:~# zpool list                                                                                  
no pools available 

```

If you have any advice about this situation, please didn't hesitate tell me !
Thanks&#65281;&#65281;

---

