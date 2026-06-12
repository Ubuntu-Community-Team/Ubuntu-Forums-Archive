---
title: "Fan control in Acer Aspire One"
date: 2008-11-01
forum: Hardware
---

### Post by spaceholiday on 2008-11-01
After wiping my Acer Aspire One clean and installing Intrepid, I find myself at a peculiar place while trying to apply the fan speed fix.  I hadn't used it before because I only got the computer last weekend. 

When I clicked "download" on the files listed [here]("http://n00.be/archives/758/"), I got a web page with all the text on it. Following the instructions given there, I copy the text to a gedit file, name the files exactly as they were named on the download link, and save them in /usr/local/bin. I go to the next step, to enter chmod a+x acerfand, and I get:

```
chmod: cannot access 'acerfand' : No such file or directory
```


Well, since I just made the file I know it exists. So I type in 'acerfand' and get:

```
bash: /usr/local/bin/acerfand: Permission denied
```


I have no idea what's going on. Again, I want to backtrack to remove everything I've done and try again, but if I try to delete the files from the terminal, I get:

```
cannot remove 'acerfand': No such file or directory
```


So I go to the gnome gui and I find that the owner of these files is root, and that I can't move them to the trash that way.  Also note that if I try to get to the acerfand and acer_ec.pl files through sudo gedit, all I get are completely blank text files. Not new documents, but blank ones that are named acerfand and acer_ec.pl.

Can someone please tell me where I went wrong and how to proceed?

---

### Post by danielcc on 2009-01-23
Thanks for the link. I just used it to fix my fan! I'm really not sure what you did wrong, but here is how you can do it and it will work sure fire...

save the two scripts to the desktop(right click and save link as) and run these commands in terminal

sudo cp /home/$USER/Desktop/acerfand /usr/local/bin/
sudo cp /home/$USER/Desktop/acer_ec.pl /usr/local/bin/
sudo chmod 755 /usr/local/bin/acerfand
sudo chmod 755 /usr/lcoal/bin/acer_ec.pl
sudo gedit /etc/rc.local

then add 

#Fan Patch
/usr/local/bin/acerfand

to the end of your rc.local that pops up, but before the exit0 or it will not execute!!!

once you restart your fan will be quite and only turn on when needed...

---

### Post by ceaser_salad on 2009-04-22
Hope no one minds me hijacking this thread. 

I'm having trouble installing fan control on me acer one(hardy). Heres what I get after following the instructions on here: [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

```
emile@ubuntu:~$ cd acerhdf_kmod && make
make -C /lib/modules/2.6.24-22-generic/build  SUBDIRS=/home/emile/acerhdf_kmod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/emile/acerhdf_kmod/acerhdf.o
/home/emile/acerhdf_kmod/acerhdf.c:86:27: error: linux/thermal.h: No such file or directory
/home/emile/acerhdf_kmod/acerhdf.c: In function &#8216;bind&#8217;:
/home/emile/acerhdf_kmod/acerhdf.c:255: error: implicit declaration of function &#8216;thermal_zone_bind_cooling_device&#8217;
/home/emile/acerhdf_kmod/acerhdf.c: In function &#8216;unbind&#8217;:
/home/emile/acerhdf_kmod/acerhdf.c:274: error: implicit declaration of function &#8216;thermal_zone_unbind_cooling_device&#8217;
/home/emile/acerhdf_kmod/acerhdf.c: At top level:
/home/emile/acerhdf_kmod/acerhdf.c:376: error: variable &#8216;acerhdf_device_ops&#8217; has initialiser but incomplete type
/home/emile/acerhdf_kmod/acerhdf.c:377: error: unknown field &#8216;bind&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:377: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:377: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:378: error: unknown field &#8216;unbind&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:378: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:378: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:379: error: unknown field &#8216;get_temp&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:379: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:379: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:380: error: unknown field &#8216;get_mode&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:380: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:380: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:381: error: unknown field &#8216;set_mode&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:381: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:381: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:382: error: unknown field &#8216;get_trip_type&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:382: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:382: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:383: error: unknown field &#8216;get_trip_temp&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:383: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:383: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:384: error: unknown field &#8216;get_crit_temp&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:384: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:384: warning: (near initialisation for &#8216;acerhdf_device_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:422: error: variable &#8216;acerhdf_cooling_ops&#8217; has initialiser but incomplete type
/home/emile/acerhdf_kmod/acerhdf.c:423: error: unknown field &#8216;get_max_state&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:423: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:423: warning: (near initialisation for &#8216;acerhdf_cooling_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:424: error: unknown field &#8216;get_cur_state&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:424: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:424: warning: (near initialisation for &#8216;acerhdf_cooling_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c:425: error: unknown field &#8216;set_cur_state&#8217; specified in initialiser
/home/emile/acerhdf_kmod/acerhdf.c:425: warning: excess elements in struct initialiser
/home/emile/acerhdf_kmod/acerhdf.c:425: warning: (near initialisation for &#8216;acerhdf_cooling_ops&#8217;)
/home/emile/acerhdf_kmod/acerhdf.c: In function &#8216;acerhdf_init&#8217;:
/home/emile/acerhdf_kmod/acerhdf.c:552: error: implicit declaration of function &#8216;thermal_cooling_device_register&#8217;
/home/emile/acerhdf_kmod/acerhdf.c:553: warning: assignment makes pointer from integer without a cast
/home/emile/acerhdf_kmod/acerhdf.c:558: error: implicit declaration of function &#8216;thermal_zone_device_register&#8217;
/home/emile/acerhdf_kmod/acerhdf.c:559: warning: assignment makes pointer from integer without a cast
/home/emile/acerhdf_kmod/acerhdf.c: In function &#8216;acerhdf_exit&#8217;:
/home/emile/acerhdf_kmod/acerhdf.c:579: error: implicit declaration of function &#8216;thermal_zone_device_unregister&#8217;
/home/emile/acerhdf_kmod/acerhdf.c:584: error: implicit declaration of function &#8216;thermal_cooling_device_unregister&#8217;
make[2]: *** [/home/emile/acerhdf_kmod/acerhdf.o] Error 1
make[1]: *** [_module_/home/emile/acerhdf_kmod] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [default] Error 2
emile@ubuntu:~/acerhdf_kmod$ 


```

Does this help?

Thanks

---

### Post by ceaser_salad on 2009-04-24
bump

---

### Post by ceaser_salad on 2009-04-26
anyone?

---

### Post by TalkHero on 2009-07-10
> **danielcc said:**
> Thanks for the link. I just used it to fix my fan! I'm really not sure what you did wrong, but here is how you can do it and it will work sure fire...

save the two scripts to the desktop(right click and save link as) and run these commands in terminal

sudo cp /home/$USER/Desktop/acerfand /usr/local/bin/
sudo cp /home/$USER/Desktop/acer_ec.pl /usr/local/bin/
sudo chmod 755 /usr/local/bin/acerfand
sudo chmod 755 /usr/lcoal/bin/acer_ec.pl
sudo gedit /etc/rc.local

then add 

#Fan Patch
/usr/local/bin/acerfand

to the end of your rc.local that pops up, but before the exit0 or it will not execute!!!

once you restart your fan will be quite and only turn on when needed...

I did this and did a restart and my fan is still going. Is there way i can see my system temp and so you know what the temp threshold is for the fan to kick in?

Edit - I have BIOS 3301, is that way it isn't working? Would upgrading the BIOS be an even better fix as i have read later ones have fan control built in?

If someone can point me towards the best way of doing this that would be great as i don't want to brick my AAO. Actually, are the instructions here good:

[http://www.techdc.com/aspire-one-bios-update-version-3304](http://www.techdc.com/aspire-one-bios-update-version-3304)

But using the BIOS 3310 from the acer website here:

[http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1486462948](http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1486462948)

Oh and finally, if i do boot off the USB stick can i just put the BIOS folder onto the same stick i put Ubuntu on, or should i re-format the stick again?

---

### Post by TalkHero on 2009-07-10
Well the BIOS updated perfectly fine, but that fan still seems quite noisy and on all the time unless that is the HDD i can hear...

---

### Post by TalkHero on 2009-07-10
Well i followed the instructions here:

[http://ubuntuforums.org/showpost.php?p=7273893&postcount=59](http://ubuntuforums.org/showpost.php?p=7273893&postcount=59)

and that seems to have made the fan alot quieter, although the AAO does seem to be a fair bit hotter, and i have yet to hear the fan kick in.

Edit - Ok, i have put iplayer on to give it something cpu heavy to do and the fan has indeed rammed up its speed. Hopefully that will be enough to cool it whilst iplayer is running (not in full screen).

---

### Post by TalkHero on 2009-07-10
> **TalkHero said:**
> Well i followed the instructions here:

[http://ubuntuforums.org/showpost.php?p=7273893&postcount=59](http://ubuntuforums.org/showpost.php?p=7273893&postcount=59)

and that seems to have made the fan alot quieter, although the AAO does seem to be a fair bit hotter, and i have yet to hear the fan kick in.

Edit - Ok, i have put iplayer on to give it something cpu heavy to do and the fan has indeed rammed up its speed. Hopefully that will be enough to cool it whilst iplayer is running (not in full screen).

Ok, after a reboot the fan now is stopping and starting every 5 seconds. Any suggested help please?

Edit: for now i have commented out the line:

   <username> ALL= NOPASSWD: /usr/local/bin/acerfand

From the file opened by running:

sudo visudo

I'm working through these tips to see if any work:

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=8900](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=8900)

---

### Post by LewRockwell on 2009-07-10
Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

---

### Post by TalkHero on 2009-07-15
Anyone got any other tips on fan control to change the temp threshold it kicks in?

---

### Post by micdhack on 2009-09-11
I have an acer aspire one model AOD150. The acerfand doesnt work for me:
```
Sep 11 22:50:55 micdhack-netbook acerfand: acerfand 0.07 starting
Sep 11 22:50:55 micdhack-netbook acerfand: Detected bios version V1.09
Sep 11 22:50:55 micdhack-netbook acerfand: Unsupported bios version V1.09 found. Aborting.

```
The bios version is the latest from the website of acer

---

### Post by MountainX on 2010-06-24
I am looking for a fan solution for the Acer Aspire One 532h (or Gateway LT2115u or LT* series).

From all the pages I've read, I cannot guess if acerfand will work. Anyone tried it?

---

### Post by Tootler on 2011-07-18
Update:

If you update your BIOS to 3310, you may find acerfand will not work. This is because the highest bios version supported by acerfand is 3309 so the script needs modifying.

The modifications can be found here: [https://help.ubuntu.com/community/AspireOne/110L?action=show&redirect=AspireOne110L#Fan%20Control](https://help.ubuntu.com/community/AspireOne/110L?action=show&redirect=AspireOne110L#Fan%20Control)

Geoff

---

