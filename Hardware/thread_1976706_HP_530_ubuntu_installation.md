---
title: "HP 530 ubuntu installation"
date: 2012-05-09
forum: Hardware
---

### Post by vector192000 on 2012-05-09
I feel the problem in hand is somewhere between laptop troubleshooting and ubuntu 
installation but not quite sure which one. 

Here are some quick facts regarding the machine i'm trying to work with:

Fact #1: HP 530 notebook. It's the machine I'm trying to install ubuntu into.

Fact #2: The DVD drive has died for the last year or so. 

Fact #3: Allong with it seems to be any means to boot besides the system's hard drive
         ( no usb key option boot in bios. Hard drive and DVD only )

An vague idea bordering the insanity I was having about a temporary 
workaround in this is pretty much this:

-Step #1: Using this ( [http://www.linuxliveusb.com/help/guide/using-lili](http://www.linuxliveusb.com/help/guide/using-lili) ) to 
          create a workable linux usb key.

-Step #2: Use grub2 to boot it. 
          ( this can actually be tricky. Ideas on how to? objections ? )
          On a sidenote this probably the last point of no return, 
          the host os still is intact....

-step #3: ???

-step #4: profit ;-)

The reasons that makes me rant about it instead of bashing it untill it 
works among others are pretty much straightforward:

1) The last time I actually worked over a linux installation was over 6 years 
   ago and... well.... linux world has certainly changed into a whole 
   different kind of dimention (=i have no idea from where to actually start).

2) My workaround sounds so far fetched that has actually given me migranes every time 
   I pick it up to sork on it. 

   Setting up a distro 6 years ago could be rather complex in order to be 
   done right ( and still remains afaik in several ways ).

3) I actually wanted to talk about it fist instead of regretting about it 
   later. Maybe i can actually get a few hints / tips / leads allong the 
   way. Or a more 'elegant' solution.

---

### Post by mips on 2012-05-09
You should be able to boot a usb stick on that laptop.

Reboot and press F10 to access the bios.
Go Advanced-->Boot options

```
Boot Otion
F10 and F12 delay (sec) : [ 5 ]
CD-Rom Boot : Enable 
Floopy Boot : Enable 
internal Network adapter boot : Disable
Boot mode : PXE 

Multiboot : Enable
   Express Boot Popup Delay : [ 10 ]

Boot Order:
   Optical Disk Drive : 1 
   USB CD-ROM : 2
   USB FLoppy : 3
   USB Superdisk :4
   Notebook Hard drive :5
   USB Hard disk : 6
   Network controller : 7
```

Save the changes and exit

Reboot the laptop with the USB memory stick inserted. Just after the BIOS screen loads you will get a menu with boot options, Select "USB Hard Disk"

If the BIOS does not recognise the usb stick there wont be a option. How did you create the usb flash stick? I have found that using unetbootin does not always work on my laptop so use "dd" instead to write the image to the flash stick.


If the above still does not work then you could always remove the hdd from the laptop, install it in a normal desktop pc (laptop uses standard sata interface, and it aeasily removed) and do the install on the desktop to the laptop hdd.

---

### Post by vector192000 on 2012-05-09
Will try them. Thank you for the reply.

---

### Post by vector192000 on 2012-05-17
Ok. Tried the instructions you provided. 

Twice, to be sure i was doing everything right. The process gave results and i now have a working lubuntu linux inside a old 4GB kingston flash drive. 

And yes, it seems to be working good this far ( i didn't have much time to thoroughly test it this far,real life gets in the way of testing it thoroughly :P ).

Another attemt i made with two Adata flash drives wasn't successfull though. Repeatetly.  Which can imply vendor specific reasons ( =adata design issues ) or just the laptop not "seeing" them during startup ( =HP bios issues ).

My bet goes to stick manufacturer issues as far as that unebootin remark you gave ( anything kingston related i got this far for the past 6 years has been sturdy, and i have been a rather harsh taskmaster ).

All in all it works though and it is my opinion than a second "thank you" is in order for the help you provided. 

So thank you. Again.

---

