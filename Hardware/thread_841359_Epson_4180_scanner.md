---
title: "Epson 4180 scanner"
date: 2008-06-26
forum: Hardware
---

### Post by Bulova on 2008-06-26
Hi Everyone:

I'm a newbie and I've just made the switch to Ubuntu and I love it!

The only hardware I can't get working is my Epson 4180 scanner. Does anyone have a solution? 

[Avasys corp]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") has linux drivers for the 4180, but I don't understand what they're are telling me. 

They list at least three downloads in the 4180 section. I need one/some/all of those?

Once I make the download how do I configure Ubuntu to recognize the driver?

Thanks for reading.

Regards,

Frank

---

### Post by phidia on 2008-06-26
Have you been to the sane site for [your scanner]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=4180&bus=any&v=&p=")? it says there that you need a non-free driver for that scanner-not sure if that's the one you linked or not.

After looking at that page you linked just scroll down select your model and debian, other and you should be ok. 
If I'm missing something here please provide more specifics (the three downloads-what are they labeled?)

---

### Post by Bulova on 2008-06-26
Yes, the sane site points to Avasys site.

I spent a lot of time on that site and I'm still not sure what they are telling me. They have scanning software that I have to use? And that only works with their driver? What is the sequence of events I need to do get this working?

If there is some documentation on this on the Avasys site, it's sure hiding on me.

---

### Post by phidia on 2008-06-26
I don't know anything about the avasys site or the business behind it. The sane homepage and the specific howtos there are your best resource.
If you open a terminal and type scanimage -L what is the ouput?

---

### Post by Bulova on 2008-06-26
I ran the scanimage and said it was not installed. So I installed it.

Then I ran the scanimage-L and it says:

"found USB scanner (vendor=0x04b8 [EPSON], product=0x0118 [EPSON Scanner]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage."

The 4180 does not seem to be supported. Is there a generic driver I could try?

---

### Post by phidia on 2008-06-26
Take a look at post #8 at [this thread]("http://ubuntuforums.org/showthread.php?t=594951") and see if that can work for you. I know that thread refers to a different version of ubuntu but it may work anyway.

---

### Post by Bulova on 2008-06-26
Phidia:

Thanks. There seems to be some information in that thread i could try.

One final question. Nobody says which file folder those rpm and plugins should be in. After downloading they go in the sane.d folder? 

What does attaching the plugin file mean? Sorry, that's two questions.

---

### Post by phidia on 2008-06-26
I didn't go through every step in the howto but I did see that you need to convert the rpms with alien. Alien is a package converter that takes rpm packages, in this case, and converts them to deb packages. It doesn't matter where the rpm's go-those files are like .exe or dmg files and once the system has installed them you can trash them.
You need to convert them though and then follow the howto for installing them (usually using dpkg)

---

### Post by Bulova on 2008-06-26
Phidia:

OK. The fog is starting to lift.

Thanks for taking the time to help.

Regards,

Frank

---

