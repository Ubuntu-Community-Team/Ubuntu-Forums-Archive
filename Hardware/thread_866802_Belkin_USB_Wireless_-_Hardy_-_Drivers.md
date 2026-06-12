---
title: "Belkin USB Wireless - Hardy - Drivers?"
date: 2008-07-22
forum: Hardware
---

### Post by tigerplug on 2008-07-22
Hey everyone, 

I installed Gutsy on my GF computer last night but the computer is too far from the router to run a cable in my situation. However, it is not too far for wireless.


I picked up a Belkin G+ wireless USB adapter but it doesn't seem to work with Gutsy.
I'm just wondering will this device work out of the box with Hardy?
If not then how will I get it working?

---

### Post by tigerplug on 2008-07-22
Again guys - If anyone can help me at all I would really appreciate it.

I would assume I need to go ahead and install nDis wrapper from the Ubuntu CD.

Then get the .INF file (Windows Driver) - Which I cannot extract from the .exe
**----------**

Has anyone got any idea how I can get the .INF - downloads are offered in .exe only.

**----------**


Assuming I get the I.INF file I need to blacklist any Belkin Drivers on the Box correct? - How do I do this and how do I know which ones to Blacklist?




Thanks


Tigerplug

---

### Post by blackaardvark on 2008-07-23
I had loads of trouble with my Belkin + Feisty/Gutsy, I eventually used serialmonkey drivers which kind of worked.

I will look for the posts that helped me but I'm using Hardy now and _it is supported out of the box_!

EDIT: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Good luck with it.

---

### Post by james_vanb on 2008-07-24
I've used the Belkin Wireless USB in both Gutsy and Hardy.  Install has been the same using ndiswrapper and the Belkin install CD.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist

```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :


```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

### Post by tigerplug on 2008-07-25
thanks guys! I got it working in the end

---

### Post by jerryduk on 2008-08-08
> **tigerplug said:**
> Hey everyone, 

I installed Gutsy on my GF computer last night but the computer is too far from the router to run a cable in my situation. However, it is not too far for wireless.


I picked up a Belkin G+ wireless USB adapter but it doesn't seem to work with Gutsy.
I'm just wondering will this device work out of the box with Hardy?
If not then how will I get working?
I have just installed Hardy 8.04  and it detected my Belkin USB wireless adapter without any problem. I didn't need a wrapper or any special drivers. It just worked. Wonderful!

---

### Post by soad6 on 2009-02-03
ok...hi ...im fairly new to linux but have used a few times with a dual-boot of windows xp ...but besides that i told my friend about it and he installed it and it works fine the problem lies with the adapter he has... it works fine in winVista (piece of ****) but when i try to run it in linux i get nothing it doesnt even recognize that he can do wireless... it says edit wireless thats all. the adapter is a belkin F58053 wireless N (mimo) and its linux 8.04 (Hardy) i know it uses rt 73 drivers to work from previous checks and other but not exactly sure how to do the Ndiswrapper part exactly...**NEVERMIND about the Ndiswrapper part i figured that part out. So ill try the same commands for the G+ adapter on the N adapter and hopefully thatll work...** If not ill tell him to go get the G+ adapter from belkin...hopefully this will be my only problem. Thanx=D>

---

### Post by tigerplug on 2009-02-05
> **soad6 said:**
> ok...hi ...im fairly new to linux but have used a few times with a dual-boot of windows xp ...but besides that i told my friend about it and he installed it and it works fine the problem lies with the adapter he has... it works fine in winVista (piece of ****) but when i try to run it in linux i get nothing it doesnt even recognize that he can do wireless... it says edit wireless thats all. the adapter is a belkin F58053 wireless N (mimo) and its linux 8.04 (Hardy) i know it uses rt 73 drivers to work from previous checks and other but not exactly sure how to do the Ndiswrapper part exactly...**NEVERMIND about the Ndiswrapper part i figured that part out. So ill try the same commands for the G+ adapter on the N adapter and hopefully thatll work...** If not ill tell him to go get the G+ adapter from belkin...hopefully this will be my only problem. Thanx=D>


Sorry I can't be of any more assistance on this as I no longer have the wireless adapter that I used Ndiswrapper for.

Perhaps someone else here can shed some light on it? ---- **BUMP**




Tigerplug ;)

---

### Post by soad6 on 2009-02-13
oops!! sorries! i fixed this issue it was fairly simple just use the drivers on the disk and ndisgtk. It worked fine! Im currently now trying to resove the issue with an acer aspire and its Nvidia 7000M graphics card... it seems supported but wont load compiz but if you have any info message me about it thanx

---

