---
title: "touchpad is not working"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by _Alik on 2007-01-22
Hi! I have a problem with touchpad on HP 500 notebook, running Ubuntu 6.10. Touchpad never worked, also on live CD and after installation and complete update, it's still not working. I try to install gsynaptics and make it run, but it also don't work after I add SHMConfig line to xorg.conf and restart. Have you any idea what to do ? As I know, this notebook is delivered to asian countries and it's linux ready.. But touchpad is not working for me :confused: 
Thanks for any help with this.

---

### Post by mikewhatever on 2007-01-22
This is very strange, cause I also have HP 5000, and the touchpad worked from the start, but not great. It got better after gsynaptics installation. Do you use Ubuntu 6.10, or 6.06?

---

### Post by Pobega on 2007-01-22
> **mikewhatever said:**
> This is very strange, cause I also have HP 5000, and the touchpad worked from the start, but not great. It got better after gsynaptics installation. Do you use Ubuntu 6.10, or 6.06?

He says in his initial post that he's running Ubuntu 6.10 :P

---

### Post by mikewhatever on 2007-01-22
Yes, I must have missed it. Could it be, that they make different touchpads for HP 5000? Alik, what's the full name of your HP? Mine is HP Pavilion DV5269ea. Just want to see if there is any difference.

---

### Post by _Alik on 2007-01-23
> **mikewhatever said:**
> Yes, I must have missed it. Could it be, that they make different touchpads for HP 5000? Alik, what's the full name of your HP? Mine is HP Pavilion DV5269ea. Just want to see if there is any difference.

Hi, no is't not HP 5000, it's [HP 500]("http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?&lang=en&cc=us&prodTypeId=321957&prodSeriesId=3264343&lang=en&cc=us&jumpid=hpr_R1002_USEN"). I know this is strange, cause I had never any problem with touchpads on others NB. For sure I check on maintenance manual for specification of this touchpad, but only info is that IRQ12 use Synaptics PS/2 Touchpad.
Today I will check older version of Ubuntu 6.06 and also others distributions of linux.

---

### Post by _Alik on 2007-01-27
So finally I found sollution on Gentoo forum. It's needed to do a little kernel hacking and compile a new kernel.

The problemmatic file is the drivers/input/serio/i8042.c in the linux kernel source. The ps/2 port detection routine erroneously thinks that there is no ps/2 port for the touchpad in my hp500 notebook. This routine resides in function i8042_check_aux(). After I put a Code:
return 0;
line in the beginning of the body of this function the touchpad worked correctly.

If anybody has the same problem,here is the patch for 2.6.18 kernels to disable the erroneous port detection routine.

Code:

--- /usr/src/linux-2.6.18-gentoo-r4/drivers/input/serio/i8042.c 2006-12-19 13:25:35.000000000 +0100
+++ /usr/src/linux/drivers/input/serio/i8042.c  2007-01-03 23:12:21.000000000 +0100
@@ -604,6 +604,9 @@
        unsigned char param;
        static int i8042_check_aux_cookie;
 
+printk("eger detektalas megkerulese\n");
+return 0;
+
/*
  * Check if AUX irq is available. If it isn't, then there is no point
  * in trying to detect AUX presence.
@@ -628,7 +631,6 @@
 
        param = 0x5a;
        if (i8042_command(&param, I8042_CMD_AUX_LOOP) || param != 0x5a) {
-
/*
  * External connection test - filters out AT-soldered PS/2 i8042's
  * 0x00 - no error, 0x01-0x03 - clock/data stuck, 0xff - general error

---

### Post by Lmasters on 2007-02-09
Excuse me,.. i have a question..

the procedure is:

1) edit the file 18042.c /linux/drivers/input/serio/i8042.c by this way:


/*
 * Internal loopback test - send three bytes, they should come back from the
 * mouse interface, the last should be version. Note that we negate mouseport
 * command responses for the i8042_check_aux() routine.
 */

return 0;



	param = 0xf0;
	if (i8042_command(&param, I8042_CMD_AUX_LOOP) || param != 0xf0)
		return -1;
	param = mode ? 0x56 : 0xf6;
	if (i8042_command(&param, I8042_CMD_AUX_LOOP) || param != (mode ? 0x56 : 0xf6))
		return -1;
	param = mode ? 0xa4 : 0xa5;
	if (i8042_command(&param, I8042_CMD_AUX_LOOP) || param == (mode ? 0xa4 : 0xa5))
		return -1;

	if (mux_version)
		*mux_version = param;

	return 0;
}

********************************** or this way
*********************************

/*
 * Internal loopback test - send three bytes, they should come back from the
 * mouse interface, the last should be version. Note that we negate mouseport
 * command responses for the i8042_check_aux() routine.
 */

	return 0;
}


2) Excuse me, but i don't know nothing of .C

3) After edit the file by the (any way 1 or 2), i have to compile the kernel 2.6.18 ?

4) [http://www.zonasiete.org/docs/kernel_mini_howto/](http://www.zonasiete.org/docs/kernel_mini_howto/) (It's in Spanish)

5) Thanks to all, i'm new in Ubuntu and it's seems to me, that is a Very Very Interesting Operative System.

Please Help..!!! :(

---

### Post by ikariwths on 2007-02-11
hi,i am new user and i am facing tha same problem with this notebook from hp ,hp500(rq260aa)
the touchpad isn't working at all.
can you help me resolve it?
i really don't won't to return to windows...

because i don't know any command's i would like someone to write the exact steps.
thank you for your time

---

### Post by _Alik on 2007-02-13
Hi, I'm working on manual. I will post link here, hope to finish it until 19.2.2007. Please be patient.

---

### Post by zaazu48 on 2007-02-13
I also have the same problem.... and I am waiting to know how to go about it......

---

### Post by Lmasters on 2007-02-13
Thanks Alik!!!

=D>

---

### Post by zaazu48 on 2007-02-14
hello,

were you able to get it to work..... because of this I went through a painful experience.... compiling a new kernel and it is still not working..... I think I didnt do some thing right

---

### Post by mottalli on 2007-02-17
Hi,
Thanks for the help, I tried the change in the kernel and it worked! 
However, it looks like the new kernel doesn't detect my wireless card (eth1). Any suggestions on this? I'm using ubuntu feisty hoard 4.

PS: If the change doesn't work, you probably changed the wrong line since there are two lines that are very similar. You need to add the "return 0" line in the function i8042_check_aux().

---

### Post by Lmasters on 2007-02-18
Hi Mottalli

I tried the change in the kernel but doesn't worked... i dont know why?..  :( 

Can u put your manual here or write the correct code in the correct line?

Thanks..

:)

---

### Post by _Alik on 2007-02-18
hi guys!
look on [this ]("http://hp500.xf.cz/")page, I created quick HowTo for HP500 resolution and touchpad problems. I will post on more informations stepwise.
Good luck! :)

---

### Post by mottalli on 2007-02-19
_Alik:
Thanks A LOT for the help, I was able to run at 1200x800 perfectly :)

Now I'll see if I can make the damned wifi work...

---

### Post by zaazu48 on 2007-02-19
How long can we wait... you know you did a great job.....

---

### Post by mottalli on 2007-02-19
For the wireless problem, I did a dmesg and I found this:

$ dmesg | grep ipw2200
[   14.520000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   14.520000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.524000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   14.572000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   14.572000] ipw2200: Unable to load firmware: -2
[   14.572000] ipw2200: failed to register network device
[   14.572000] ipw2200: probe of 0000:02:04.0 failed with error -5

Looks like a problem with firmware? What could this mean?

---

### Post by mottalli on 2007-02-19
Hey guys!

I got the wifi card working! The problem is that after recompiling the kernel, the firmware for the card and other hardware is not copied to a directory with the same name as the new kernel.

In order to fix this, you just need to make a symlink in the /lib/firmware directory that points to the firmware files of the old kernel.

For example, my old kernel was called "2.6.20-8-generic" and my new kernel is called 2.6.20-ubuntu1hp500. In that case, I did the following (as root):

# cd /lib/firmware
# ln -s 2.6.20-8-generic 2.6.20-ubuntu1hp500

Reboot and voilá!

_Alik: feel free to post this info on your great page :)

---

### Post by _Alik on 2007-02-20
mottalli:
GREAT! WIFI IS WORKING NOW! =D> Thanks for solution, I will post it on page and hope to put there more information to HP500.

---

### Post by topbot on 2007-02-20
Thank you very much, Alik and mottalli.

---

### Post by Lmasters on 2007-02-20
Thanks  Guys...

:)
I'm working with my touchpad...

Alik.. Congratulations by your Page.. it's very completed..

Mottalli: Thanks for this information...

---

### Post by ikariwths on 2007-02-21
thank you for the solution,i'll trie it when you write a more detailed way of turning on  the wifi on your web page.(new user)
thank's again

---

### Post by ikariwths on 2007-02-24
i have tha same problem after updating the kernel i dont longer have wifi,can anyone PLEASE help me enable it?i am a new user so i need the exact steps
help please 
thank you

---

### Post by mottalli on 2007-03-01
> **ikariwths said:**
> i have tha same problem after updating the kernel i dont longer have wifi,can anyone PLEASE help me enable it?i am a new user so i need the exact steps
help please 
thank you

take a look at my post in here:
[http://ubuntuforums.org/showthread.php?t=344103&page=2](http://ubuntuforums.org/showthread.php?t=344103&page=2)

---

### Post by zaazu48 on 2007-03-09
Hello Forumer,
    please dont be offended... has anyone tried to to patch ipw2200 driver for aircrack... after recompiling his/her kernel.... if so please tell me how.... any way am running kubuntu 6.10... any help will be appreciated

---

### Post by rohom on 2007-03-18
> **mottalli said:**
> Hey guys!


For example, my old kernel was called "2.6.20-8-generic" and my new kernel is called 2.6.20-ubuntu1hp500. In that case, I did the following (as root):

# cd /lib/firmware
# ln -s 2.6.20-8-generic 2.6.20-ubuntu1hp500

Reboot and voilá!



:confused:  Where can i find my old and new versions of kernel?

---

### Post by ikariwths on 2007-03-20
> **rohom said:**
> :confused:  Where can i find my old and new versions of kernel?

hello again,im writting you from windows xp:( because i haven't manage to set up the touchpad! the instructions on your page didn't do the trick...
i dont't know why,but at the end(after compiling the kernel) is giving me an error,it says that it dosent find the image or something like that
any help?

---

### Post by rohom on 2007-03-21
> **ikariwths said:**
> hello again,im writting you from windows xp:( because i haven't manage to set up the touchpad! the instructions on your page didn't do the trick...
i dont't know why,but at the end(after compiling the kernel) is giving me an error,it says that it dosent find the image or something like that
any help?

I've a similar trouble solved. Try to reinstall all GCC (especially in trick mentioned).

---

### Post by ikariwths on 2007-03-22
> **rohom said:**
> I've a similar trouble solved. Try to reinstall all GCC (especially in trick mentioned).



is it simple?what packeges i have to reinstall?should i write only gcc in synaptics?

---

### Post by ikariwths on 2007-03-22
> **ikariwths said:**
> is it simple?what packeges i have to reinstall?should i write only gcc in synaptics?

do you think that at the new version of ubuntu the toucpad will work?
because if it is going to work then i should avoid formating for now

---

### Post by rohom on 2007-03-23
> **ikariwths said:**
> is it simple?what packeges i have to reinstall?should i write only gcc in synaptics?

Go to terminal and just do it:
*sudo aptitude remove gcc-4.1*
This string will gone some dependencies - answer yes for all, then:

*sudo aptitude install gcc*
and maybe another next strings from trick

---

### Post by topbot on 2007-03-26
hi, I updated to feisty and the touchpad problem reappeared. I tried to look at i8042.c in the new kernel, but it has a different structure now, the code was rewritten. Anyone has any clues?

---

### Post by phiber102 on 2007-04-02
hi heres a guide to activate touch pad on your laptop 
[http://hp500.xf.cz/us/Main.html](http://hp500.xf.cz/us/Main.html) 
but when i did it my touchpad worked wonderful but i lost my wireless connection :( wich im working atm to fix

---

### Post by topbot on 2007-04-02
I think I need to specify what my problem is.
I mean, has anyone looked at i8042.c from 2.6.20? The code is completely different, and probably I am too stupid to understand its logic right away. I tried inserting return 0; in a place that seemed logical to me (after the i8042_check_aux was announced as the original gentoo forum thread suggested), but it did not work for me. Has anyone had this problem?

---

### Post by vij on 2007-04-04
> **topbot said:**
> I think I need to specify what my problem is.
I mean, has anyone looked at i8042.c from 2.6.20? The code is completely different, and probably I am too stupid to understand its logic right away. I tried inserting return 0; in a place that seemed logical to me (after the i8042_check_aux was announced as the original gentoo forum thread suggested), but it did not work for me. Has anyone had this problem?

  Hi,

  On my 2.6.20 distro I edit drivers/input/serio/i8042.c source, line #550 (i8042_check_aux function), and add 

  return 0;

  After compilytion and installing of the new kernel touchpad works.


  Regards

---

### Post by topbot on 2007-04-04
thanks, vij, I will try it when I get home.

---

### Post by stonedraccoon on 2007-04-10
i just got an hp500 and it's also my first time with ubuntu. it's really cool that this forum exists as i have ready answers to my problems with the resolution and the touchpad. thanks everybody! more power to you! :)

---

### Post by rami on 2007-04-12
> **mottalli said:**
> Hey guys!

I got the wifi card working! The problem is that after recompiling the kernel, the firmware for the card and other hardware is not copied to a directory with the same name as the new kernel.

In order to fix this, you just need to make a symlink in the /lib/firmware directory that points to the firmware files of the old kernel.

For example, my old kernel was called "2.6.20-8-generic" and my new kernel is called 2.6.20-ubuntu1hp500. In that case, I did the following (as root):

# cd /lib/firmware
# ln -s 2.6.20-8-generic 2.6.20-ubuntu1hp500

Reboot and voilá!

_Alik: feel free to post this info on your great page :)

So I installed the new kernel and got the touchpad to work, however there is only one kernel in /lib/firmware ...which is the old one.:confused: 

:confused: Whats wrong?? Thanks in advance :)

---

### Post by rami on 2007-04-12
> **mottalli said:**
> Hey guys!

I got the wifi card working! The problem is that after recompiling the kernel, the firmware for the card and other hardware is not copied to a directory with the same name as the new kernel.

In order to fix this, you just need to make a symlink in the /lib/firmware directory that points to the firmware files of the old kernel.

For example, my old kernel was called "2.6.20-8-generic" and my new kernel is called 2.6.20-ubuntu1hp500. In that case, I did the following (as root):

# cd /lib/firmware
# ln -s 2.6.20-8-generic 2.6.20-ubuntu1hp500

Reboot and voilá!

_Alik: feel free to post this info on your great page :)

So I installed the new kernel and got the touchpad to work, however there is only one kernel in /lib/firmware ...which is the old one.:confused: 

:confused: Whats wrong?? Thanks in advance :)

---

### Post by mottalli on 2007-04-12
> **rami said:**
> So I installed the new kernel and got the touchpad to work, however there is only one kernel in /lib/firmware ...which is the old one.:confused: 

:confused: Whats wrong?? Thanks in advance :)

Rami: that's exactly the problem, that *only* the old kernel is in /lib/firmware. You will have to create a symlink in that directory with the name of the new kernel, that points to the old one.

---

### Post by rami on 2007-04-13
> **mottalli said:**
> Rami: that's exactly the problem, that *only* the old kernel is in /lib/firmware. You will have to create a symlink in that directory with the name of the new kernel, that points to the old one.

I tried doing that...I had a hard time figuring the name of the new kernel.

I did this:
> sudo ln -s 2.6.17-10-generic 2.6.17-14-ubuntu1_hp500

and this (the name of the kernel when booting):
> sudo ln -s 2.6.17-10-generic 2.6.17.14-ubuntu1

None worked. I also made sure that only one symlink is available, i.e rm the first one before doing the second one :confused:

---

### Post by rami on 2007-04-13
Oh well I deleted all symlinks, restarted and symlinked using the second command (without hp500). And it worked!!

:KS thanks ya'll:KS

---

### Post by rami on 2007-04-21
So recompiling the kernel for Feisty just doesn't cut it, has anybody found a solution for Feisty yet??


PS: I will recompile again I might have done something wrong :)

---

### Post by mottalli on 2007-04-24
> **rami said:**
> So recompiling the kernel for Feisty just doesn't cut it, has anybody found a solution for Feisty yet??


PS: I will recompile again I might have done something wrong :)

rami: the fix works fine in Feisty, you just have to put the "return 0;" line in the function i8042_check_aux() and recompile

---

### Post by rami on 2007-04-25
Great it worked. You are a life saver motalli!! 

Aparently I was puting the return ;0 on the line 608, I should've known I shouldn't follow that guide to a tee! And I should start learning programming languages!!!

Thanks a lot!!:popcorn:

---

### Post by dgl on 2007-05-13
If it makes it easier for anyone I've rebuilt the standard Ubuntu kernel, details [here]("http://use.perl.org/~dgl/journal/33263"). This has the same version number so saves dealing with the firmware breakage as well as saving a recompile.

---

### Post by gian_nuke on 2007-05-16
thank you very much dgl!
you're kernel rocks on my hp510 with feisty... :guitar: 

I hope that these problems will be solved with new releases of the kernel... :tongue:

excuse for my bad english... :lolflag:

---

### Post by gian_nuke on 2007-05-18
> **dgl said:**
> If it makes it easier for anyone I've rebuilt the standard Ubuntu kernel, details [here]("http://use.perl.org/~dgl/journal/33263"). This has the same version number so saves dealing with the firmware breakage as well as saving a recompile.

well... I've a new problem... :(
with an *aptitude upgrade* ubuntu overwrite the dgl's *linux-image* package with the ubuntu's *linux-image* package, and, after reboot, the touchpad stop to work...
so I've re-installed dgl package: *dpkg -i linux-image-2.6.20-15-generic_2.6.20-15.27_i386.deb*
but uptitude ask me again to update this package.
surfing the web I discovered the pin...
so I've set my /etc/apt/preferences
```
Package: linux-image
Pin: version 2.6.20-15-generic 
Pin-Priority: 1001
```
I've also tried with version:
2.6.20
2.6
2.6.10-15
2.6*
but it doesn't work...
how can I fix it?

after that I discover that *linux-image* seems that is not installed ò.O
```
ryo@brooke:~$ dpkg -l linux-image
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
ryo@brooke:~$
```
what's wrong?
pin prevent from upgrade, or from install (or both) ?

excuse for my bad english... I hope you understand... ^^

---

### Post by dgl on 2007-05-18
Seems like building it with exactly the same version number isn't such a clever idea. I've added dgl to the version so it is treated as a newer version than the one currently in Ubuntu. This solves the update problems.

It's here:
[linux-image-2.6.20-15-generic_2.6.20-15.27dgl_i386.deb]("http://dgl.cx/2007/05/ubuntu-hp510/linux-image-2.6.20-15-generic_2.6.20-15.27dgl_i386.deb")

BTW, the kernel packages are slightly more complex than most normal packages because the kernel is designed to support multiple versions in case there is a problem with one (which by using the same version number I've bypassed, bad me, I can assure you I've tested the packages though..). Therefore if you did need to pin one you should pin both the linux-image-generic package (depends on a package with a specific version, updated for major updates) and the linux-image-2.6.20-15-generic package which is the specific version.

---

### Post by gian_nuke on 2007-05-19
> **dgl said:**
>  Seems like building it with exactly the same version number isn't such a clever idea. I've added dgl to the version so it is treated as a newer version than the one currently in Ubuntu. This solves the update problems.

It's here:
[linux-image-2.6.20-15-generic_2.6.20-15.27dgl_i386.deb]("http://dgl.cx/2007/05/ubuntu-hp510/linux-image-2.6.20-15-generic_2.6.20-15.27dgl_i386.deb")

BTW, the kernel packages are slightly more complex than most normal packages because the kernel is designed to support multiple versions in case there is a problem with one (which by using the same version number I've bypassed, bad me, I can assure you I've tested the packages though..). Therefore if you did need to pin one you should pin both the linux-image-generic package (depends on a package with a specific version, updated for major updates) and the linux-image-2.6.20-15-generic package which is the specific version.

ok! linux-image-2.6.20-15-generic_2.6.20-15.27dgl_i386.deb works great!
thank you very much!

---

### Post by bofphile on 2007-05-20
I was having the same problem but with another laptop (Packard Bell Easynote 3281W) and now with your new kernel package, my touchpad works just fine.
Thanks a lot !

---

### Post by fijam on 2007-05-21
Has this been submitted upstream? Is it still required to patch the driver in, say .22rc1?

---

### Post by rzelnik on 2007-05-27
I have updated the kernel to the official 2.6.20-16-generic and the touchpad is working now! :p

---

### Post by ksiv on 2007-07-31
Hi all, could you please tell me what does it mean "WIFI WORKS". 
1. Driver is loaded
2. Firmware loaded
3. Hardware RF Kill switch disables radio

Is I only one why has Hardware RF Kill switch in HP 500 
Part num: RQ260AA#ACB

---

### Post by topbot on 2007-07-31
"hw kill switch on" either means you meed to enable your wifi in the bios or press that blue wifi button near the power switch.

---

### Post by ksiv on 2007-07-31
Hi everyone, one more time and Sorry for off-top, but i should continue as someone started IPW2200 on HP 500 issue here. 

This info could be possible very usefull for some of us. 

After installing 
- a new kernel (it solves the touchpad issue as well) 
-  fresh drivers 
- new firmware (about version 3)
- dmesg output shows the card , the appropriate device is made  
some guys cross the problem their WiFI does not work. Surprisengly enough the rest wonder "What could be wrong? it works nice". (So called WorksForMe state in QA)

Finally I solved the problem but in very strange way.

 Actually those who suffers from WIFI lack have the following simptoms:
1) The Radio button (left to power one) keeps black except the moment after power is on. Pushing in on working mashine results nothing.
2) dmesg contains next two rows
ipw2200: Radio Frequency Kill Switch is On: 
Kill switch must be turned off for wireless networking to work

How these guys got into such a trouble?
1) They reinstalled the system removing WinXP too fast
OR
2) Get rid of it without care of HP Wireless Assistant  WiFI state

HP Wireless Assistant("WA" herein)
 is a Win application responsible for Hardware RF Switch

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3264343&prodNameId=3264344&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-46007-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3264343&prodNameId=3264344&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-46007-1)

The solution is: 
0) Read information how to reinstall your  boot loader if any
1) Install windows on free partition
2) Install WiFi Driver
3) Install HP WA
4) Use HP WA to enable WIFI (Ask it go from tray, keep sure it is turned on AND enabled )
5) Reboot to your debian installation (or another name you use for your linux)

On Windows Reboot you will see the blue wifi button, in Linux you will be able to use this button after boot.
iwconfig will show "radio off / unassociated" for button states black/blue respectivelly.

The radio keep working after reboot, hibernate, poweroff. I have not  tried a battery removal yet.

I use Linux version 2.6.22-rc4


Thanks for reading such a long post. Hope it will help to some Linux users.

---

### Post by ksiv on 2007-07-31
> **topbot said:**
> "hw kill switch on" either means you meed to enable your wifi in the bios or press that blue wifi button near the power switch.

WIFI was enabled in BIOS all the time in my case, Thanks

---

### Post by homogenizer on 2007-08-14
Greetings,

I assume fiesty has a patch for the HP500 business notebook.  At first it is not working.  After completing the synaptic updates.. the touchpad is working perfectly w/o recompiling the kernel.

---

