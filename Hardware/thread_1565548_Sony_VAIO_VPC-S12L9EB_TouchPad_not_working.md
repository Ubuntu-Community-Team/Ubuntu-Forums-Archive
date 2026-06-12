---
title: "Sony VAIO VPC-S12L9E/B TouchPad not working"
date: 2010-09-01
forum: Hardware
---

### Post by karry on 2010-09-01
Dear colleagues,

That's my first post...I've recently bought a VAIO S12 series, unfortunately it does not work "out of the box" with 10.04 but I've fixed many issues.

The biggest problem I have by the moment is within touchpad as it's not working.

Do you have any idea about how to fix it?

Thanks in advance!

---

### Post by zecapistolas on 2010-09-01
Hello karry, welcome aboard.... :D

I have the same [problem]("http://ubuntuforums.org/showthread.php?p=9784980#6"), recently i buy new laptop, Sony Vaio VPC-S12M9E/B....

I try everything, but don't work.... :(

---

### Post by userlambda on 2010-09-09
Same pb with my VPC-S12V9E and an up-to-date ubuntu 10.10

---

### Post by zecapistolas on 2010-09-09
Solution:

> 
1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot


Now my touchpad work's great.... :KS

---

### Post by userlambda on 2010-09-09
Thank you Zecapistolas,

in the mean time I found the same fix in another thread, except that there was only i8042.nopnp to add,
and it works. Do you know what the other stuff i8042.reset, nomux, noloop do for you?

---

### Post by zecapistolas on 2010-09-10
> **userlambda said:**
> Thank you Zecapistolas,

in the mean time I found the same fix in another thread, except that there was only i8042.nopnp to add,
and it works. Do you know what the other stuff i8042.reset, nomux, noloop do for you?

Yes, with only i8042.nopnp touchpad work's....

No, i don't know what is i8042.reset, nomux, noloop... :D

---

### Post by userlambda on 2010-09-10
OK so I will stick to the minimal change.

I still have two pbs with my installation and I have started a new thread that might be relevant to you also:

[http://ubuntuforums.org/showthread.php?t=1571866](http://ubuntuforums.org/showthread.php?t=1571866)

;)

---

### Post by Leshinsky on 2010-09-10
I feel dumb.  I have a sony vaio vpcee23fx and im having touch pad and 10 key problems.  I found this post but am confused how to do the edit feature of the below solution.  Can anyone please help.  Thank you in advance.

Solution:

 	Quote:
 	 	 		 			 				1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

---

### Post by karry on 2010-09-10
It worked for my VPCS12L9E...thanks very much!!!! but now I have many other things to fix...microphone, bluetooth...do you have same problems?

---

### Post by Leshinsky on 2010-09-10
I was more asking how you do this
Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop
as i get very confused sometimes.  Does anyone know, or can make it more simple for me.  Thanks so much.

---

### Post by userlambda on 2010-09-15
The reason why you cannot edit the grub file is maybe that you were not root?
If this was the pb. use "sudo" before the edit command

---

### Post by Beobachter on 2010-09-15
This GRUB editting has fixed my friend's MSI VR630 laptop, too. Now his touchpad works just fine. Thanks!!

---

### Post by empoulator on 2010-09-19
Dear Leshisky,

to edit grub, open a terminal (applications => system tools).
And type sudo nedit /etc/default/grub
Then you can add the command if it does not exist already.

For the others: I had many troubles with Ubuntu 10.4, so I decided to try the beta version Ubuntu 10.10. It worked fine (e.g. I could use Rosegarden with midi files, by typing timidity -iA first, I had the graphic card Nvidia and touchpad working right from the beginning). The GRUB_CMDLINE_LINUX="i8042.nopnp" was already included in Grub.

BUT - and this is the reason of my post -  I tried many things, but I can't DEACTIVATE  the touchpad. This seems to be a common problem. Maybe some of you will have a solution for the Sony Vaio... What I tried until now didn't work. I still can't see the touchpad in System => Mouse. 

Any idea ?

---

### Post by Luca1729 on 2010-09-21
Karry,

Did you manage to get the microphone working? I have a VPC-S12C7E and I have managed to get much of it working, but one of the things I would really like to use is the internal microphone and it doesn't work.

Luca

---

### Post by rohit88 on 2010-10-01
thanks...it worked!! but i cant use my edge scroll on touchpad...can u help me with it

---

### Post by Luca1729 on 2010-10-03
I am using VPC S12 C7E but the edge scroll, whilst a bit temperamental, works okay.

---

### Post by nuclearb on 2010-10-04
THANK YOU! it worked great!

---

### Post by kkpickel on 2010-12-05
I'm getting this error when I put in 

bash: /etc/default/grub: Permission denied

Does anyone know why my access is denied and how I can fix this?

---

### Post by peertje888 on 2010-12-15
kkpickel: IMHO the thread is very clear on this...you have to open the file as super user, you can do this by using either su, sudo or gksudo. For example from shell:

```
sudo gedit /etc/default/grub
```

or from your desktop -> run application (Alt + F2)

[HTML]gksudo gedit /etc/default/grub[/HTML]

---

### Post by stevekh3 on 2010-12-17
Thank you works fine also on my [B]Sony Vaio VPC-F13Z1E/B.
[/B]

---

### Post by Stevan on 2010-12-28
This solution worked for my Sony VAIO VPC-F132FD. (PCG-81114L)

QUOTE
1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot 
END QUOTE

Thanks

---

### Post by ifindturtles on 2010-12-31
> **zecapistolas said:**
> Solution:



Now my touchpad work's great.... :KS

Thanks a lot, my touchpad now works!

---

### Post by jamescarr on 2011-01-09
For the past 2 months I've been forced to use my VPC-EA3X5E
 with a usb mouse. After finally unearthing this post I am able to use my touchpad. 

Thanks a lot! :)

---

### Post by fandango11 on 2011-01-11
thanx so much....touchpad works

---

### Post by millij on 2011-02-09
This works perfectly.. 

Thanks & Regards.

---

### Post by hai2lp on 2011-02-26
i have sony vaio vpc-yb15AG but still doesn't work,

:(

---

### Post by fannyfazit on 2011-02-27
This also worked for my notebook: Schenker Xesia, E500 2EC, using Ubuntu 10.04 LTS

>  1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

Thanks

---

### Post by xtremedeep on 2011-03-07
> **zecapistolas said:**
> Solution:



Now my touchpad work's great.... :KS

Thanks Buddy... It works on my E41FX.. now for the other things that are bugging me.. 

Xtremedeep:KS

---

### Post by flana on 2011-04-21
I have Sony Vaio VPCEA36FM, and the talked about solution above did not work for me.

PLEASE HELP!!!

---

### Post by Luca1729 on 2011-04-22
Hi all,

I had a go with the test version of 11.04 and had a much better experience with my Vaio. I haven't tested everything but the microphone did work (but with some static type noise) which is a first for me (even after downloading and compiling ALSA). When it is fully released next week I might have another go.

---

### Post by flana on 2011-04-22
BTW... so a few things to note

1. Make sure you do not edit the grub file as a text file, which is what i was doing. so I then used sudo gedit /etc/default/grub. 

2. Make sure you run the sudo update-grub after the file has been saved.

After all these the touch pad worked.

Now I hope the next weeks release works with UBUNTU installed on SD, AND the x64 ISO works as well.

Currently for me, ubuntu boots only when installed on an external USB hard drive. USB Pendrive or an SD card installs but fails to boot. Also x64 has not worked yet. So keeping my fingers crossed

---

### Post by nidhin joseph on 2011-06-23
i have a sony vaio lap with named series vpceb34en. i installed ubuntu 10.04 amd64 bit os. my lap touchpad is notworking and sound also not working. but in windows these all are working fine. anyone please help me. i am in hell, i need to work more ............please help................

---

### Post by badkrash on 2011-06-26
Hi,
I have a Sonly Viao VPCEB490X. Since I upgraded from Ubuntu 10.10 to 11.04, my touchpad stopped working. I have a dual boot with Win7 on another partition. And the touchpad has stopped working even on that partition and no fixes on the windows end work either. I have tried everything possible (including adding 18042.nomux, nopnp, reset etc. to grub commands as discussed in this thread) and still the problem persists. 

When I call Sony tech support, their recommendation is to install the OS that the computer comes with (Win7 home) and that's no good. I am forced to use a USB connected mouse now.

Please help!!
--Nihil

---

