---
title: "Ubuntu/linux compatible UPS"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by wpshooter on 2007-01-13
Is there any company that is currently making a UPS that has automatic shutdown software with a GUI that will run natively on a Ubuntu O/S ?

Thanks.

---

### Post by e_klektic on 2007-02-23
I'm just investigating now. I was suprised to find nothing in the forums. I desparately need a UPS for my Ubuntu server.

I've found a project called NUT which has compatibility with many UPSs and is still active:
[http://www.networkupstools.org/compat/stable.html]("http://www.networkupstools.org/compat/stable.html")

There is also a HOWTO on the Linux Documentation Project - last updated 2005-09-28 - this even contains a buying guide:
[http://tldp.org/HOWTO/UPS-HOWTO/index.html]("http://tldp.org/HOWTO/UPS-HOWTO/index.html")

Finally, it seems that APC provide proprietary Powerchute software for their UPSs for "business use":
[http://www.apcc.com/tools/download/software_comp.cfm?sw_sku=SFPCBE705&id=125&family=&part_num=&swfam=125]("http://www.apcc.com/tools/download/software_comp.cfm?sw_sku=SFPCBE705&id=125&family=&part_num=&swfam=125")

I hope this helps.

---

### Post by yabbadabbadont on 2007-02-23
There isn't a GUI in the repositories that I'm aware of, but apcupsd works fine with all newer USB APC UPS's.  (ahhhhh acronym overload :))

It runs as a system service and will shutdown the system properly if the power goes out for too long.  I've got mine configured to shutdown the system if there is either only 5% left in the battery or 5 minutes of battery time left.

Edit: Yikes!  I just realized that the OP's question was asked over a month ago...

---

### Post by e_klektic on 2007-02-23
Which is about how long I've been running a serious doc management system with no UPS!

APC are calling me back.

---

### Post by wpshooter on 2007-03-05
> **e_klektic said:**
> Which is about how long I've been running a serious doc management system with no UPS!

APC are calling me back.

Well, I hope your conversation with APC bares better results than mine.

According to my past conversations with them, they do not have any shutdown software for Ubuntu O/Ss.

As I remember, I have asked them about the APCUPSD software mentioned in one of the link in an previous post and they told me that that is not nor do they support that product.

I think I am going to call them again and ask if they are yet to offer any software support for Ubuntu O/Ss.

Thanks.

---

### Post by e_klektic on 2007-03-05
Hold on. I've bought the APC UPS now and installed it. I haven't quite got around to looking at software. I'll open the packet, see what is provided then edit this post.

Right, yes, I'm afraid you're right. Here is the list of compatible Linux versions on the APC PowerChute CD:
The PowerChute Business Edition Agent is compatible with 
	Red Hat Linux Professional 7.3, 8.0, 9.0; 7.3J, 8.0J, 9.0J
	Red Hat Linux AS 2.1, 3.0; 2.1J, 3.0J
	Red Hat Linux ES 2.1, 3.0; 2.1J, 3.0J
	Red Hat Linux WS 3.0; 3.0J
	Turbolinux® Server 8.0; 8.0J; 10.0; 10.0J
	SuSE Linux Professional 8.2, 9.0, 9.1 (not supported in Japan)
	Miracle Linux 2.1J, 3.0J (only in Japan)
	Novell® NetWare® 6.0, 6.5 (not supported in Japan)
	Solaris 8, 9; 8J, 9J

      - The PowerChute Business Edition Agent installs and requires Sun 
      Microsystems' JVM 1.4.2_06

They don't support apcupsd, [http://www.apcupsd.org/](http://www.apcupsd.org/) but that is what I'm planning on using.

I used the following:
root@ubuntu-Linux:~# apt-cache search apcupsd
apcupsd - APC UPS Power Management
apcupsd-cgi - Cgi for APC UPS Power Management
apcupsd-doc - Documentation for apcupsd

So it is available from the repositories.

Hope this helps all who visit.

Rich

---

### Post by wpshooter on 2007-03-05
Rich:

I called APC again this morning and they told me that they still have not yet started supporting Ubuntu O/Ss.  **BUT**, that it is possibly being considered.

I believe that if enough Ubuntu users would take 10 to 15 minutes out of their day to call APC and possibly the other major UPS manufacturers about this, we could possibly get a decent UPS shutdown package with a good GUI, that you did not have to reinvent the wheel in order to get it to work.

If the Ubuntu users are NOT willing to do this, then they have no one but themselves to blame when the power goes off while they are away and they wind up with a crashed O/S, and dead battery on the UPS.

Thanks.

---

### Post by yabbadabbadont on 2007-03-05
Why do you need a gui?  apcupsd works fine.  Power goes off, when the ups hits the minimum time or battery percentage left, apcupsd shuts the system down.

---

### Post by wpshooter on 2007-03-06
> **yabbadabbadont said:**
> Why do you need a gui?  apcupsd works fine.  Power goes off, when the ups hits the minimum time or battery percentage left, apcupsd shuts the system down.

So I don't have to download and study a 214 page PDF file in order to get the program setup and running correctly.  

Thanks.

---

### Post by yabbadabbadont on 2007-03-06
> **wpshooter said:**
> So I don't have to download and study a 214 page PDF file in order to get the program setup and running correctly.  

Thanks.

You have to change four or five lines in /etc/apcupsd/apcupsd.conf for a single machine connected to a single UPS...  :roll:

---

### Post by wpshooter on 2007-03-06
> **yabbadabbadont said:**
> You have to change four or five lines in /etc/apcupsd/apcupsd.conf for a single machine connected to a single UPS...  :roll:

Is this described in the 214 pages ?  And if, so is it clearly labeled/indexed or do you have to read thru most of the 214 pages to find it ?

Also, once you get this running, if you do not have a GUI, how do you know it is functioning properly unless you just wait to see if it is still functioning when you happen to lose power ?

Thanks.

---

### Post by yabbadabbadont on 2007-03-06
The config file is very well commented.  I just checked the online manual and there is even a quickstart for beginners section.  (Did you even look at the docs?  ;))

[http://www.apcupsd.org/manual/Planning_Your_Installation.html#SECTION00061000000000000000](http://www.apcupsd.org/manual/Planning_Your_Installation.html#SECTION00061000000000000000)

---

### Post by wpshooter on 2007-03-13
[QUOTE=yabbadabbadont;2257260]The config file is very well commented.  I just checked the online manual and there is even a quickstart for beginners section.  (Did you even look at the docs?  ;))

[url]http://www.apcupsd.org/manual/Planning_Your_Installation.html#SECTION0006100

No, not yet.  Except for the section on supported O/Ss.  And I don't see Ubuntu listed unless it is covered under one of the other selections.  Is it ?

Thanks.

---

### Post by MetalMusicAddict on 2007-03-13
Im with yabbadabbadont here. I just connected my APC UPS's to my 3 machines and Ubuntu handled the rest. I actually had a power outage and with no config the 3 machines all shutdown gracefully when power got low. Theres even notifications in the taskbar when it goes to battery like it was a laptop.

I have 3 ES-500's.

---

### Post by wpshooter on 2007-03-13
> **yabbadabbadont said:**
> There isn't a GUI in the repositories that I'm aware of, but apcupsd works fine with all newer USB APC UPS's.  (ahhhhh acronym overload :))

It runs as a system service and will shutdown the system properly if the power goes out for too long.  I've got mine configured to shutdown the system if there is either only 5% left in the battery or 5 minutes of battery time left.

Edit: Yikes!  I just realized that the OP's question was asked over a month ago...

Does this software have the ability to ALSO shutdown the power drain for the UPS itself, so that if the electricity is off for an extended period of time to keep the battery on the UPS from being completely drained ???

My Belkins have this feature if they are being run on a M/S O/S and if they have the Belkins M/S compatible software installed.

Is there any Linux based software that has this ability ???  It is good if the APC software shuts down the computer gracefully but if the UPS battery is then drained down and ruined by the other attached items, then only half the job has been done.

Thanks.

---

### Post by MetalMusicAddict on 2007-03-13
> **wpshooter said:**
> It is good if the APC software shuts down the computer gracefully but if the UPS battery is then drained down and ruined by the other attached items, then only half the job has been done.

Thanks.

Its actually better that the battery is fully discharged rather than partially then recharged. You can shorten a battery's capacity that way.

---

### Post by wpshooter on 2007-03-13
> **MetalMusicAddict said:**
> Im with yabbadabbadont here. I just connected my APC UPS's to my 3 machines and Ubuntu handled the rest. I actually had a power outage and with no config the 3 machines all shutdown gracefully when power got low. Theres even notifications in the taskbar when it goes to battery like it was a laptop.

I have 3 ES-500's.

When you say Ubuntu handled the rest, you mean it handled the configuration, after you installed the APCUPSD from Synaptic, correct ?

Thanks.

---

### Post by MetalMusicAddict on 2007-03-13
> **wpshooter said:**
> When you say Ubuntu handled the rest, you mean it handled the configuration, after you installed the APCUPSD from Synaptic, correct ?

Thanks.

I dont remember installing it but yes. Its there. :) I for sure know I didnt touch a config.

---

### Post by wpshooter on 2007-03-13
> **MetalMusicAddict said:**
> I dont remember installing it but yes. Its there. :) I for sure know I didnt touch a config.

What version of Ubuntu are you running ?

I just looked on two of my Dapper machines and APCUPSD is NOT installed by default.

Thanks.

---

