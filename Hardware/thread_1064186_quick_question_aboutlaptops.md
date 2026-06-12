---
title: "quick question aboutlaptops"
date: 2009-02-08
forum: Hardware
---

### Post by cmay on 2009-02-08
hi.
i just got a new laptop and i installed ubuntu in it . i will post it on the hardware compatibles list once i clear this simple queston as it works simply out of box with everything.  even the wireless is just working right after installing. 
question is. sometimes it takes around 20 sec to boot up and get to login screen. and sometimes it takes around 10 sec to get to a black screen that stands for about anohter maybe even 30 sec or sometimes 40 sec then a short flash of some text message in terminal and then login screen. what is doing this. 
the specs from the add on the x-one i got. 
[PHP]
"15.4" TFT widescreen (WXGA/ GT 1280 x 800)
intel dual core T1600 (1.66 ghz)
160 gigabyte harddisk
2 gigabyte ddr-2 ram
dvd /rw dual layer 
1.3 mega pixel webcam
a wireless netcard
and a 4000Ah battery
[/PHP]
thanks for the time :).

---

### Post by Yashiro on 2009-02-10
It's probably network related. Try giving your ethernet port a fixed address even if you don't use it.

---

### Post by martinbaselier on 2009-02-10
I would advise to edit /boot/grub/menu.lst and remove quiet and splash, so you can see where it pauses.

---

### Post by cmay on 2009-02-10
thanks for the replies. i think i know whats up then. there is a sim card for wireless installede but i have an eye operation coming up soon so i dont see that well and my brother have not have time to fix that yet. so it must be that it is trying to cennect to i think.

 i have installed the ubuntu studio -rt kernel instead of the intrepid ibex generic but it has nothing to do with that. i i think i will just post all the specs i got on it in the hardware compatibles list since it works straight out of the box with intrepid ibex. 

if this is not somekind of problem as such due to hardware i can do that with out posting somehting that is not right. 

thanks for the time.

---

### Post by cmay on 2009-02-17
[PHP]# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp[/PHP]
output of the blacklisted modules. it has not been doing this for sometime now only once in a while. i think i found the reason. it matches with the behavior since when it loads up and the screen is howering black it has not found the sound and when the terminal out quickly flashes its loading timiditi which i think is something to do with sound settings. 

 i am going to post all the specs on this laptop as complete compatible and mention this issue just tonight when i have some time to this.  i fond out about this by chance from trying to figure someting else out.

---

