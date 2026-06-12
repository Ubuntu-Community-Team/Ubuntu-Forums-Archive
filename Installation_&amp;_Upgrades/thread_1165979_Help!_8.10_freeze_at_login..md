---
title: "Help! 8.10 freeze at login."
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by Mr_Cus on 2009-05-21
Hi all, 
This is my first post here but been reading for a while. I'm a bit of a newbie and dont know many terminal commands etc 

Basically, my problem is that i've upgraded from 8.04 to 8.10 and when ever i get to the login screen (just before actually when the screen is still all white) it freezes. From what i've read it sounds like a graphics problem and i think it probably is because the rotating 'loading mouse' is very blocky. Does anyone know how i can overcome this problem?

I read somewhere that it was possible to change some settings using the grub root shell prompt but when i try to acess this it requires a password (or ctrl-D) to continue. The problem with this is im sure i've never set a password so cant access the prompt.

Really stuck so any help would be gratefully appreciated.

Thanks, Marcus

I'm running an HP2133 mininote by the way.

---

### Post by b@sh_n3rd on 2009-05-21
Hi...It *does* seem to be a graphics issue..what video adapter do you have on your PC?
The root password is the same password you use to login...
I'm not sure of the "loading mouse" thingy though...It could just be another symptom to one prob...

Oh yeah, and welcome to the community! :D

---

### Post by Mr_Cus on 2009-05-21
> **b@sh_n3rd said:**
> Hi...It *does* seem to be a graphics issue..what video adapter do you have on your PC?
The root password is the same password you use to login...
I'm not sure of the "loading mouse" thingy though...It could just be another symptom to one prob...

Oh yeah, and welcome to the community! :D

Hi, thanks for your reply :D,
i think the video adapter is chrome 9? would that sound right to you?

As for the password I thought thats what it was but when i enter my password and press enter the same line comes up again asking for my password or ctrl-d to continue. puzzling!!!

Is there anyway to change the resolution ubuntu loads up in by using the command prompt  grub>   ?

Thanks again

---

### Post by b@sh_n3rd on 2009-05-21
Hi, If it's a VIA video adapter, then it does...It's got a problem with Ubuntu 8.10...Jaunty has no problem I *think*. Anyway, I made a friend on the forum by helping him fix it :D..

Check this link to setup your card: [http://help.ubuntu.com/community/OpenChrome](http://help.ubuntu.com/community/OpenChrome)
Go here for your bug fix, you may have to scroll down abit: [https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions]("https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions")

Hope this helps :D..(It *should*)

PS: [I]I had a feeling you could be having a VIA card coz the symptoms rang a bell :D

[/I]**EDIT:** Oh yeah, I usually set the resolution in GRUB to about, 1024x768...for this you've gotta edit the "/boot/grub/menu.lst" file...Add "vga=792" in after "quite splash" (the end of "kernel:") at the bottom (not for recovery mode kernel)..This would give you 1024x768...it's really cool and pleasing...
To edit menu.lst, ```
# gksudo gedit /boot/grub/menu.lst
```

---

### Post by b@sh_n3rd on 2009-05-21
Here's a sample of the resolution option if you want it...
```

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2f9ddac9-053e-4ed6-ad59-12cb6a79fe58
[COLOR=Navy]kernel        /vmlinuz-2.6.28-11-generic root=UUID=6e43d2bf-df32-4b9c-8d9f-b7b6fd2b1d18 ro xforcevesa quiet splash[/COLOR] **[COLOR=Green]vga=792[/COLOR]**
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2f9ddac9-053e-4ed6-ad59-12cb6a79fe58
kernel        /vmlinuz-2.6.28-11-generic root=UUID=6e43d2bf-df32-4b9c-8d9f-b7b6fd2b1d18 ro xforcevesa  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2f9ddac9-053e-4ed6-ad59-12cb6a79fe58
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```The above is from Jaunty so it might be slightly different, nothing much but the kernel version...I've coloured the line you need to add "vga=792" to...(You will have to scroll down to the bottom for this section...it's the last...above this are all samples and a few other options, some of which I'm clueless about :D)

---

### Post by Mr_Cus on 2009-05-21
> **b@sh_n3rd said:**
> 

Check this link to setup your card: [http://help.ubuntu.com/community/OpenChrome](http://help.ubuntu.com/community/OpenChrome)
Go here for your bug fix, you may have to scroll down abit: [https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions](https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions)

[/code]

I checked out these links and pretty sure i can follow the instructions given but ( and this will probably prove my newbieness) do i not need to be able to access a terminal to do those commands? 

I've changed the resolution  but this doesnt seem to have made much difference, i still cant get to the point of typing in my username at the login screen. I think the resolution has deffinitely changed though because the mouse appears in a different area of the screen now. 
Do yo uthink it would be worth skipping 8.10 and trying 9.04?

---

### Post by b@sh_n3rd on 2009-05-21
Sorry, I think you'd better try the fix first before anything else...I'll tell you what to do and how right here, 
When you boot your PC, hit "ESC" at the GRUB (where it says, "ESC to view menu" or something to that effect with a countdown) menu and select "Recovery Mode" (within brackets, should be the 2nd option)...then, choose to login to a root shell at the menu (because your PC freezes at GDM, it maybe impossible to enter the console via "CTRL+ALT+F2". This is a fool proof method so you won't be wasting any time :D). Then at the prompt type,
```
# sudo nano /etc/X11/xorg.conf
```Over here, scroll down to 'section "device"' Then, edit it as follows;
```
Section "Device"
        Driver    "openchrome"
        Option    "XaaNoImageWriteRect"
EndSection
```After editing, hit "CTRL+X", then "Y", then hit enter. You should now be back at the prompt...now just type, ```
# sudo reboot
``` to reboot your PC.

Now you should get to GDM without any probs...After this, you can try to optimize your video as mentioned...Hope this works...
*Note that you won't have anything to do with GUI at this point!!*

---

### Post by Mr_Cus on 2009-05-27
> **b@sh_n3rd said:**
> Sorry, I think you'd better try the fix first before anything else...I'll tell you what to do and how right here, 
When you boot your PC, hit "ESC" at the GRUB (where it says, "ESC to view menu" or something to that effect with a countdown) menu and select "Recovery Mode" (within brackets, should be the 2nd option)...then, choose to login to a root shell at the menu 


Thank you so much for your help up to now and sorry for my late reply.

Still having problems accessing anything so i'll write down what i have and what i do.

I get to the grub menu by pressing esc and then i have a list of kernels:

ubuntu 8.10, Kernel 2.6.27-14-generic
ubuntu 8.10, Kernel 2.6.27-14-generic (recovery mode)
ubuntu 8.10, Kernel 2.6.24-24-generic
ubuntu 8.10, Kernel 2.6.24-24-generic (recovery mode)
ubuntu 8.10, Kernel 2.6.24-23-generic
ubuntu 8.10, Kernel 2.6.24-23-generic (revovery mode)
ubuntu 8.10, Kernel 2.6.24-16-generic
ubuntu 8.10, Kernel 2.6.24-16-generic (recovery mode)
ubuntu 8.10, memtest86+ 

at this point i'm not sure which recovery mode kernel to use(?) 

I highlight the 27-14 recovery kernel and press 'c' which takes me to a command prompt that looks like this

grub>

I am then unable to make anycomands work except the ones offered when i press tab.

I hope that makes sense..?  I'm so so stuck on this one :(

Thanks again:KS

---

