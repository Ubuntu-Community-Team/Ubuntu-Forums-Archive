---
title: "Boot problem on Asus Expert Book"
date: 2024-05-29
forum: Hardware
---

### Post by klamigro on 2024-05-29
[]("https://askubuntu.com/posts/1515444/timeline")  
          
                                        I have an Asus Expert Book BA15400 laptop. I installed KUBUNTU  parallel to Windows 11. KUBUNTU 23.10 worked fine. There was just the problem, that after  suspendig the computer could not restart. It could be the same problem  as here: [ubuntu 22.04 is not waking up from suspend]("https://askubuntu.com/questions/1514103/ubuntu-22-04-is-not-waking-up-from-suspend").


 After updating to KUBUNTU 24.04 this problem occurs at every boot.  After choosing KUBUNTU in the Boot menu (GRUB), the screen turns black with  backlight on. It shortly switches off the backlight and turns it on  again. This is the point, where the UBUNTU lock-in screen should appear. The  computer seems to be working but does not react to anything. 


 The only way to start UBUNTU is by using the recovery mode. In recovery mode the system starts. After directly rebooting from a running session started in recovery mode, the system starts  even without recovery mode. When i choose "shutdown" and turn the  computer on afterwards, it doesn't work.


 About the issue, that the system doesn't start after suspending, i  had tried UBUNTU 23.10, Manjaro and Mint half a year ago with the same result.  Now I didn't try to go back  to an older version yet. Windows works normally.

 I don't know, whether there is a connection to the following issue:
 If i try to use fsck in the recovery menu, it shows the following error: /lib/recovery-mode/recovery-menu: Zeile 80: /etc/default/rcS: Datei oder Verzeichnis nicht gefunden (File or folder not found) fsck von util-linux 2.39.3 /dev/nvme0n1p6 ist eingehängt. (mounted) e2fsck: Fortsetzung nicht möglich, wird abgebrochen. (continuation impossible, is terminated)

 

 Does anyone have an idea what i could do? If more information is  needed, tell me. Unfortunately i don't have a deep knowledge about  operating systems.

 Thanks a lot!

---

### Post by currentshaft on 2024-05-30
32OWr

---

### Post by klamigro on 2024-06-02
Currentsahft, many thanks for your advice. 
It works, after removing "quiet splash" the computer starts normally. But, when i press "e" at the next boot the "quiet splash" is back again in the parameters.
So do i need to change the grub.cfg and update the grub config, right? I  found the description, how to do that.
Does that change have any effects (except that i can start the system)?
Thanks again!

---

### Post by Rubi1200 on 2024-06-02
To make the change permanent you need to edit your GRUB config file.

Remove quiet splash, save, run update-grub.

Let us know if it still works for you.

---

### Post by klamigro on 2024-06-03
It worked! I added a config to /etc/default/grub.d and updated grub.
Now the computer starts normally. Waking up from suspend mode seems still not to work. But that's less important.
Thanks a lot!

---

