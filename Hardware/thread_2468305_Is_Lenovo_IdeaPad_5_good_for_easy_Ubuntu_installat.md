---
title: "Is Lenovo IdeaPad 5 good for easy Ubuntu installation?"
date: 2021-10-25
forum: Hardware
---

### Post by erosman on 2021-10-25
I was offered a Lenovo IdeaPad 5 i5(i7)-1135G7 8(16)GB 512GB SSD NVIDIA Geforce MX450.

Would I be able to install Ubuntu 21.10 on it hassle-free for a newbie?
There are some posts on the internet about installation issues with IdeaPad 5.


References:
- [Lenovo Launches Linux-Ready ThinkPad and ThinkStation PCs Preinstalled with Ubuntu]("https://news.lenovo.com/pressroom/press-releases/lenovo-launches-linux-ready-thinkpad-and-thinkstation-pcs-preinstalled-with-ubuntu/")
- [Ubuntu certified hardware]("https://ubuntu.com/certified?category=Laptop&vendor=Lenovo&offset=0")
- [Linux for Personal Systems]("https://support.lenovo.com/fr/fr/solutions/pd031426")

---

### Post by mIk3_08 on 2021-10-25
> **erosman said:**
> I was offered a Lenovo IdeaPad 5 i5(i7)-1135G7 8(16)GB 512GB SSD NVIDIA Geforce MX450.
Would I be able to install Ubuntu 21.10 on it hassle-free for a newbie?
There are some posts on the internet about installation issues with IdeaPad 5. I think yes. because Lenovo is now offering full certification and Linux preinstalled hardware. Here are some of the link that Lenovo supports Linux.
Click [here]("https://www.linux-magazine.com/Online/News/Lenovo-Upping-Their-Linux-Support") for more info.

---

### Post by erosman on 2021-10-25
> **mIk3_08 said:**
> I think yes. because Lenovo is now offering full certification and Linux preinstalled hardware. Here are some of the link that Lenovo supports Linux.
Click [here]("https://www.linux-magazine.com/Online/News/Lenovo-Upping-Their-Linux-Support") for more info.


Doesn't it say ...... ?
> PC giant Lenovo is bringing serious support to Linux...big support. The  entire line of Lenovo workstations (**minus the IdeaPad**) will now be fully  certified to work with Linux.

---

### Post by T6&amp;sfpER35% on 2021-10-25
i think anything will run Linux without hassle
but i'd rather install 20.04.3 , stick with LTS

"[COLOR=#111111][FONT=Ubuntu]Ubuntu 21.10 Impish Indri is the final interim release before the next Ubuntu Long Term  Support (LTS) due to be released in April 2022. Developers can use Ubuntu 21.10 to future-proof their work for the next LTS, which will be supported at least until 2032."
[https://ubuntu.com/blog/ubuntu-21-10-has-landed](https://ubuntu.com/blog/ubuntu-21-10-has-landed)
[/FONT][/COLOR]

---

### Post by mIk3_08 on 2021-10-26
> **erosman said:**
> Doesn't it say ...... ?
Even though it doesn't mention your Lenovo model but in general it will support your Hardware System. That's not a problem. 
I do have an HP laptop. They say that it won't work on Linux But here I am now using my HP laptop with Linux Ubuntu Operating System running on it. All the wifi, bluetooth, and etc are working properly. It only depends on the user how they install 
the Linux Distro Operating System on it. Not to brag you but I can run any brand of System Hardware with any Linux Distro installed on it. It will work smoothly. Good Luck and Welcome to Linux World.

---

### Post by T6&amp;sfpER35% on 2021-10-26
> [COLOR=#000000]it doesn't mention your Lenovo model but in general it will support your Hardware System. That's not a problem[/COLOR]
+1
i have a 1917 pc that i'm sure isn't listed anywhere on the interwebs to be compatible with Linux, yet here i am , on Linux
just do it ..lol

---

### Post by joor2 on 2021-10-27
No, Ubuntu probably does NOT work on an IdeaPad 5! I have an Ideapad 5i Pro (14", Intel Core i7-1165G7, Intel iRISxe, NVIDIA GeForce MX450).

The screen turns black, and stays black for more than a second _every time_ you move the mouse! Yes. It's very weird. I'ts only on the laptop's monitor, an external monitor is fine. 

 I tried Ubuntu 20.04 LTS and 21.10 (both with Gnome and KDE Plasma). But the screen kept stuttering. It has to do with the iRISxe graphics, because everything is fine when I use "safe mode" (where it uses software rendering).

Everything works fine with windows, so the laptop isn't broken or anything. It's really annoying because I bought this laptop for Ubuntu..

IF ANYONE KNOWS HOW TO FIX THIS PLEASE REPLY!!

---

### Post by mIk3_08 on 2021-10-28
> **3nd said:**
> +1
i have a 1917 pc that i'm sure isn't listed anywhere on the interwebs to be compatible with Linux, yet here i am , on Linux
just do it ..lol
Thanks 3nd. I know you already know. It always amaze us when you are in Linux Ubuntu community. So go go go Linux Ubuntu Forum community. :-) cheers.  
Regards

---

### Post by mastablasta on 2021-10-28
> **joor2 said:**
> 

IF ANYONE KNOWS HOW TO FIX THIS PLEASE REPLY!!

latest kernel.and maybe some other things (like patching kernel with oibaf PPA drivers:

[https://askubuntu.com/questions/1299067/ubuntu-20-04-no-driver-loaded-for-intel-iris-xe-graphics](https://askubuntu.com/questions/1299067/ubuntu-20-04-no-driver-loaded-for-intel-iris-xe-graphics)

[https://askubuntu.com/questions/1309561/ubuntu-20-10-how-to-use-iris-driver-with-intel-iris-xe-graphics](https://askubuntu.com/questions/1309561/ubuntu-20-10-how-to-use-iris-driver-with-intel-iris-xe-graphics)

---

### Post by mIk3_08 on 2021-10-29
> **joor2 said:**
> IF ANYONE KNOWS HOW TO FIX THIS PLEASE REPLY!!
You can try this method. Maybe this can help fix your hardware system to function smoothly using Linux Ubuntu Operating System. If you need to install a proprietary drivers just follow the instructions in the link below.
Just click [here]("https://askubuntu.com/questions/543325/how-to-download-all-required-ubuntu-drivers"). Hope it help. Good Luck and Welcome to Linux World.

---

### Post by joor2 on 2021-11-08
Thanks for all the ideas. But none of them worked. I think the driver is loaded fine. Ubuntu knows its using Intel Iris Xe graphics, they just dont work properly :(

I tried:
- oibaf drivers
- sudo ubuntu-drivers autoinstall
- oem kernel 20.04
- and with KDE Plasma I tried 60Hz and 90Hz, opengl 2.0, 3.1 and renderx (whatever that is) and all kinds of resolutions

none worked

---

### Post by joor2 on 2021-11-22
In case anyone is still reading.

I think Lenovo IdeaPad 5 has a problem that is solved in kernel 5.15:
> “There is more work to be done, but this avoids the flicker if your  display is connected to the non Intel GPU – the typical case where a  dual-GPU laptop is connected to an external monitor,”
source:  [https://9to5linux.com/collabora-brings-flicker-free-multi-gpu-boot-and-rockchip-h-264-decoder-to-linux-5-15](https://9to5linux.com/collabora-brings-flicker-free-multi-gpu-boot-and-rockchip-h-264-decoder-to-linux-5-15)

When 5.15 becomes the standard in Ubuntu, I will give Ubuntu another try.

Btw. If you are desperate: PopOs seems to work best. I only have occasional screen flickering. When I change monitor stuff (resolution, order, etc) than the flickering can become very bad. After a reboot this is gone (a side from the occasional flicker it always has)

---

### Post by dominic_mayers on 2022-09-27
Just to say that I just installed Ubuntu 22.04 on the Lenovo IdeaPad 5 15ALC05 without any problem. The touchpad works perfectly (the right click is obtained by taping with two fingers, by design). The WIFI works perfectly. It goes in sleep mode when we close the laptop and wake-up when we open it. The external mouse also works fine. The external monitor also worked fine. 

I installed it first with the LVM partition option and second with the "Erase disk and use zfs" option and it worked in both cases. I have not checked other options, but I suppose they are also fine. I had to run "sudo grub-mkconfig > ~/grub.cfg" to generate a new content for "/boot/grub/grub.cfg" to get rid of the annoying grub menu at each boot. Actually, it generated the exact same config file less the lines:

menuentry 'UEFI firmware Settings' $menuentry_id_option 'uefi-firmware' {  
     fwsetup 
}

---

### Post by kubofhromoslav on 2022-12-05
> **dominic_mayers said:**
> Just to say that I just installed Ubuntu 22.04 on the Lenovo IdeaPad 5 15ALC05 without any problem

Sir, may I ask how you have achieved this?

I am trying for 3 days to instal Kubuntu 22.10 on Lenovo IdeaPad 5 15ALC05 (82LN005FCK) using bootable USB stick (confirmed to work on other PC) but the USB stick is not even seen by the default boot loader...

---

