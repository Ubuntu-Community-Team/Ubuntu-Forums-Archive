---
title: "I could use some help"
date: 2009-12-12
forum: Hardware
---

### Post by woses21 on 2009-12-12
So here is my problem.  I bout a new laptop that had windows 7 on it and I hated it.  Nothing but problems.  So anyway, I tried going to XP, and after everything initializes and windows is starting I get a blue screen of death with the stop codes 0x0000007B (0xF78D663C, 0xC0000034, 0x00000000, 0x00000000).  I looked this up and I found the codes say this stop indicates the OS could not access the hard drive because there is no compatible driver loaded.  

I then had the brilliant idea (before I did my homework on the stop codes) that if I install something else I could format it and it would work (dumb idea).  Now, I would keep Linux for everything but I can't get some software to work right.  I run older software, mostly games like Diablo 2, Starcraft, Dark Forces: Jedi Knight, some GuildWars too. 

Now I can't get into the setup before Grub loads to change any settings, or load or even check my HDD drivers.  I was also told I could change the controller from SATA to IDE in order to read the older software.  I'm not sure what exactly I can do at this point.  My laptop is the Asus N81Vp.  Here is a link

[http://usa.asus.com/product.aspx?P_ID=JExNpew5BY4uwRKv](http://usa.asus.com/product.aspx?P_ID=JExNpew5BY4uwRKv)

Any help with getting a dual boot with XP or just setting up with Ubuntu would be greatly appreciated.  Seriously, I'll send you some cookies or something.

---

### Post by Daveth on 2009-12-12
can you clarify this please- do you now have an xp/ linux dual boot that will not boot, or just a linux install that will not boot, and is Windows 7 history on this machine?

Remember that you can always run ubuntu as a live distro and poke about in the settings from there, over the top of any installed OS, as long as you set the bios to boot from the cd drive.

---

### Post by woses21 on 2009-12-13
I have a working Ubuntu install with no dual or swap of any kind.  Windows 7 was erased on the linux install, I didn't want it anywhere near me.  My BIOS already boots from the disk and I can run the live cd, but what settings would I have to change?

---

### Post by drz4007 on 2009-12-13
just before grub loads, you can enter your bios (the pc must informe you by which button to do that [for acer it is F2]) and there you can find an option about your drives. IDE or SATA or RAID i think. just change that,save and exit and try to boot windows again. maybe you'll have to install windows again. i'm nit sure about that.

---

### Post by asmeetkumar on 2009-12-13
> **drz4007 said:**
> just before grub loads, you can enter your bios (the pc must informe you by which button to do that [for acer it is F2]) and there you can find an option about your drives. IDE or SATA or RAID i think. just change that,save and exit and try to boot windows again. maybe you'll have to install windows again. i'm nit sure about that.

AFAIK, pleaase don't change your raid settings in case you have any it will cause you a lot of trouble...

as you said you've already installed linux and your machine boots into it so there is no need to change your setup settings, keep the default ones

and to run windows programs on Linux you need to install "wine" on your system or if you are willing to purchase crossover can be a much better option (especially for running games)....

---

### Post by Fcon_Vpro on 2009-12-13
I think I experienced a similar problem with an IBM a few years back.
The option you are looking for in the bios might be called "enhanced sata" or something along those lines. Switch that option to IDE or maybe to OFF and then Windows should be able to use its own driver to load the OS instead of the manufacturer driver.
I looked at the laptop specs and there is only 1 drive so I doubt there will be a raid configuration.
Also from personal experience, always install windows before linux, as it will make life a lot easier to get grub to setup the dual boot options.

---

