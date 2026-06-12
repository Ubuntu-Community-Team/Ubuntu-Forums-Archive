---
title: "eeepc/ubuntu setup"
date: 2009-06-18
forum: Hardware
---

### Post by user_not_expert on 2009-06-18
If there are no objections, may I start an umbrella thread specifically for getting all the hardware and functions running on the eeepc? This is bound to cross-over other support categories and I know there are helpful eeepc forums out there, but as I have Linux on various machines and now 3 eeepcs in the family, I find that the eeepc has its own peculiar flavour and problem set with ubuntu and it would save a lot of trawling to share the main aspects of this in one place.

I'll kick-off with a question that goes against the flow. The world and her dog may be trying to turn wifi on, but I would like to be able to turn it off (issues of choice :D)

Even if I disable wireless-lan option in the bios, ubuntu turns it back on during boot-up.

This happens with the 900 and the 1000hd under EasyPeasy, Netbook Remix, and Studio 9.04 (with the rt kernel or generic)

it does not happen with Puppy, PC-BSD or Windows.

I haven't found a way to turn it off once running.

I have tried installing the eee aplet and the eee scripts - neither seem to give me acess to the special functions, though this may just be user ignorance if they need seting up.

Anybody with furher ideas or their own eeepc/ubuntu problems?

---

### Post by barrieluv on 2009-06-18
You could try installing Fewt's scripts which you can read more on [here](http://forum.eeeuser.com/viewtopic.php?id=63574).
They're vey popular and have been incorporated into the latest version of Eeebuntu where they have been well recieved.

Putting all the Eee stuff into one place is a nice idea, but it would almost instantly need splitting into several categories as not all EeePCs, for instance, use the same processor.  Mine is a Celeron and therefore does not support true scaling which has caused problems with scripts which insist on throttling it and my wireless card is an Atheros which supports packet injection and many of the others don't.

---

### Post by user_not_expert on 2009-06-19
Fair point,

but as a lot of people don't know how to be specific about hardware problems, if they come here they can post and get redirected, just like you redirected me :p

---

### Post by Exciterusa on 2009-06-20
> **user_not_expert said:**
> 
I'll kick-off with a question that goes against the flow. The world and her dog may be trying to turn wifi on, but I would like to be able to turn it off (issues of choice :D)

Even if I disable wireless-lan option in the bios, ubuntu turns it back on during boot-up.

I haven't found a way to turn it off once running.

Anybody with furher ideas or their own eeepc/ubuntu problems?

Can't you just go into System>Preferences>Network Connections - select wireless connection and uncheck connect automatically?
I don't have a eeepc but most laptops also have a fn combo key to disable the wireless to save battery power as well.

---

### Post by user_not_expert on 2009-06-20
> **Exciterusa said:**
> Can't you just go into System>Preferences>Network Connections - select wireless connection and uncheck connect automatically?
I don't have a eeepc but most laptops also have a fn combo key to disable the wireless to save battery power as well.

Yes, deselecting wireless connection in every dialogue box I could find was my first attempt at a solution. Everything now says its active but not configured and the blue led for wi-fi is still on.

In Ubuntu I havn't been able to get the fn combo keys to work and whether I use the rt, generic or adam's eee kernel I get the same results.

I go into bios settings and dis-activate the wireless-lan. When I boot up Ubuntu, about a third of the way through the os load, the blue led comes on and then stays on, whether I use the fn key, scripts, applets or de-selection. When I re-boot, I go into the bios and find that the wireless-lan is reset to active.

Ubuntu is the only os that does this (on my ex's 900 and my 1000HD) so I'm ruling out a problem with the pc. The bios setting is left alone and the fn key works in Win XP, PC-BSD and Toutou Linux, so I don't understand why I have so much difficulty with Ubuntu.

As Ubuntu Studio is one of the main reasons I have for buying the machine, I'm reluctant to move to a different distro, but I seem to be loosing a lot of time going nowhere on this one.:confused:

---

### Post by FlyingBuzz on 2009-06-21
Try to use eee-control. It's very useful applet that allows to switch different perfomance modes and also enable or disable camera, cardreader, bluetooth or wi-fi.
As for me (I'm using Eee PC 901 20 Gb) it remembers the latest state of Wi-Fi adapter. Of I had turned it off before shut the system down it will be turned off on startup.

---

### Post by user_not_expert on 2009-06-21
> **FlyingBuzz said:**
> Try to use eee-control. It's very useful applet that allows to switch different perfomance modes and also enable or disable camera, cardreader, bluetooth or wi-fi.
As for me (I'm using Eee PC 901 20 Gb) it remembers the latest state of Wi-Fi adapter. Of I had turned it off before shut the system down it will be turned off on startup.

Thank you, thank you,thank you.

It took me all afternoon (which kept me off the philosophy thread in the café :-?)

I found it here:

[http://greg.geekmind.org/eee-control/deb/](http://greg.geekmind.org/eee-control/deb/)

along with explanations and instructions which were in places too technical for me.

So, I installed 'python-dev' because it said I'd need it (don't know if I did or not).

Then I chose the 'Prebuilt Ubuntu packages' option and clicked on

eee-control_0.9.3_all~jaunty.deb

and 'open' on the download options and 'install' on the package installer

Each time it went wrong, I typed:

> sudo apt-get autoremove eeec-control

and started again.

I had to activate the source code repositories in

»Main Menu»System»Administration»Software Sources

and then typed 'kernel' in the search box in

»Main Menu»System»Administration»Synaptic Package Manager

which I used to install the kernel source, kernel headers and kernel package (just to be safe because I didn't know what it actually needed)

Then it installed with no problems and at last, I can switch off the wi-fi in Ubuntu. :D FlyingBuzz is right, It does remember for next boot and there's lots of things under 'preferences' including setting up a range of 'fn' things for yourself. The menu on the tray-applet depends on your eeepc apparently.

If anyone knows an easier method for installing eee-control, please post it here.

---

### Post by user_not_expert on 2009-06-21
There's the first problem soved on the **eeepc/ubuntu setup** thread. 

Next please :P

---

### Post by troie on 2009-06-23
Hello!

I'm trying to set up Ubuntu (easy-peasy) on an eeepc900. I've re-formatted using gparted to check the drives and it said everything was fine. Then, when I tried to install, I got these two messages:


>  File system has an incompatible feature enabled. Compatible features are has_journal, dir_index, filetype, sparse_super and large_file. Use tune2fs or debugfs to remove features. and:

>  The test of the file system with type ext2 in partition #3 of SCSI2 (0,1,0) (sdb) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.The test of the file system with type ext2 in partition #3 of SCSI2 (0,1,0) (sdb) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is. My mother's pc was set up exactly the same way and she didn't have this problem. I'm not a complete beginner to Ubuntu, but I'm new to the command line. Could anyone help me please?:confused:

---

### Post by barrieluv on 2009-06-23
So, using Gparted live, you deleted all partitions on both drives and reformatted both of them as as Ext2?
I would run Gparted again and right click the drives and choose 'Check' from the menu.
If this doesn't get rid of your problem, try reformatting as Ext3.  I'm assuming you want to use Ext2 because of the SSD/number of writes arguement, but it can't hurt to try it.

---

