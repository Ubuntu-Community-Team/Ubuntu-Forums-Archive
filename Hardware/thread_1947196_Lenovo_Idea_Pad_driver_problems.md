---
title: "Lenovo Idea Pad driver problems"
date: 2012-03-26
forum: Hardware
---

### Post by Seine_Lordschaft on 2012-03-26
I recently bought my new Lenovo IdeaPad Z370 without operating  system and installed Ubuntu 11.10 64 bit (the pre-installed system was  FreeDOS which I decided to remove).
 
Nearly all is working  fine. The only exception are the volume keys: pressing them does start  adjusting the volume, but causes a system problem. If I press sound up,  the speakers move to immediately to the maximum volume and behave as it I  was continuing to press the button.
 
The same happens when  pressing the volume down or sound off buttons. It is then not possible  any more to use the keyboard or type anyting, nor change the volume  using the touchpad and Ubuntu's speaker symbol. It is also not possible  any more to shut down the computer using Ubuntu's virtual shutdown  button, but with the real button on the computer.
 
The  touchpad is still working and after putting the computer briefly into  standby the problem is solved to the degree that it is possible to use  the keyboard etc. again, and the sound volume can be adjusted again with  Ubuntu's speaker symbol.
 
I guess this must be a driver issue that ubuntu 11.1 does not support the buttons.
 
As  well, the one-key-theatre button and the thermal-management button do  not work. Pressing them, just nothing happens (except that the light  up).
 
I should mention that installing Ubuntu apparently  deleted the partitions including the one-key recovery button. At least  this key does now only work like a second power-button. Unfortunately I  did not receive the User-guide with the computer but only downloaded  from the internet after installing Ubuntu.
 
I wonder  whether apart from adjusting the volume buttons, it might be possible to  get the one-key-theatre button and thermal-management-button  operational for ubuntu too, and whether the one-key-recovery button  could work under ubuntu too. Gparted tells me that I have 2 small  partitions of 3.9 GiB each, labeled "extended" and "windows swap", and  one of 1.02 GiB which is not in use apart from the main drive of course.




The Lenovo support answered the following to this problem:
> 

                                                                                                                                  
                                            The issue you are encountering is due to driver absence in Linux.
 The driver for Linux is not available.  Hope, Ubuntu new version have more applications and drivers.
  
 Best Regards,
 Tanuj



Is there any workaround or fix in Ubuntu?

---

### Post by cmavr8 on 2012-06-06
Proposed fix works: [http://ubuntuforums.org/showpost.php?p=11648013&postcount=4](http://ubuntuforums.org/showpost.php?p=11648013&postcount=4) (for the first issue you're having)

---

