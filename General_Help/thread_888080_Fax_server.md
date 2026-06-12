---
title: "Fax server"
date: 2008-08-12
forum: General Help
---

### Post by guitarman on 2008-08-12
has anyone setup a Ubuntu Fax Server.

any help would be greatly appreciated.

thanks

---

### Post by cariboo on 2008-08-12
To setup a fax server you need to install hylafax, it is available in the repositories. There is a howto here:

[http://www.cs.bgu.ac.il/~piavka/hylafax-howto/](http://www.cs.bgu.ac.il/~piavka/hylafax-howto/)

Be sure you have a modem that is supported by linux.

Jim

---

### Post by guitarman on 2008-08-12
ok thanks I will try this.  I have an 2 older external fax/modems that I use to use in the old BBS days.  Yes they still work.  My Hayes is 14400 and my GVC is 28.8k.  I will just connect one of them to the serial port and see if it gets recognized.

The idea is to be able to receive faxes (usually 8.5 x 14 legal) size and have the fax server email them to myself where I can open and print on my laser printer.  It's hard to find a SOHO affordable fax machine that will support 8.5 x 14 legal size incoming faxes.

I'll let you know how it goes.

Cheers,

---

### Post by guitarman on 2008-08-12
just tried to install it, but it does not seem to.  I found this site with distros already prepared:

[http://people.ifax.com/~aidan/apt/dists/](http://people.ifax.com/~aidan/apt/dists/)

it seems that there exists precompiled versions for all Ubuntu except Hardy Heron 8.04 that I am running.  Do I need to scale back a version or just install on a newer machine with feisty fawn or other.

any suggestions?

---

### Post by thinkdez on 2008-09-24
Not sure what you have tried so far but I just installed the server yesterday.  Provided your modem is compatible with Linux then you can install hylafax from the repositories:
```

#sudo apt-get install hylafax-server

```

After which you will need to configure hylafax using faxsetup script.

```

#sudo faxsetup

```

The faxsetup should prompt you to run faxaddmodem and take you through the setup but if it doesn't run faxaddmodem from the command line and it will help you configure it.  

Once completed restart hylafax and you should be able to send and receive faxes.

```
#sudo /etc/init.d/hylafax stop
#sudo /etc/init.d/hylafax start
```

I haven't configured it to redirect mail but that should get you started.  There is plenty of documentation at the hylafax site that will help you do what you are asking [http://www.hylafax.org/content/Documentation]("http://www.hylafax.org/content/Documentation")

Hope that helps

---

### Post by brian mcgee on 2008-11-02
> **guitarman said:**
> just tried to install it, but it does not seem to.  I found this site with distros already prepared:

[http://people.ifax.com/~aidan/apt/dists/]("http://people.ifax.com/%7Eaidan/apt/dists/")

it seems that there exists precompiled versions for all Ubuntu except Hardy Heron 8.04 that I am running.  Do I need to scale back a version or just install on a newer machine with feisty fawn or other.

any suggestions?

Check out:
[http://www.aboutdebian.com/fax.htm](http://www.aboutdebian.com/fax.htm)

To chat with your modem on /dev/ttyS0, use cu or minicom, e.g.,

```
cu -l /dev/ttyS0
```It should say connected. To see which classes your modem supports, type

```
at+fclass=?
```Then enter

To exit cu, type "~~." then enter

---

### Post by ly9000 on 2010-06-28
This link may be help you:

[http://www.howtoforge.org/forums/showthread.php?t=41911](http://www.howtoforge.org/forums/showthread.php?t=41911)

Good luck!!!

---

### Post by linuxcss on 2010-10-22
cu -l /dev/ttyACM0

when running the above I get

cu: open (/dev/ttyACM0): Permission denied
cu: ttyACM0: Line in use

I have even logged in as superuser under karmic

Any suggestions?

---

### Post by frank cox on 2013-05-02
Have you listed yourself as a modem user? Also you may need to set up PPP. Dialup networking on Ubuntu is not user friendly as it is on Puppy Linux for instance. That being said I set up dialup on many different variations of Ubuntu , never a fax though. I have some notes somewhere on the subject if you still have trouble. Another solution is to use on online fax service, they work quite well in my opinion.You might try setting up gnome-ppp from the local depositories and confiqure ppp just to see if you have the permissions correctly set.If faxing 
 with Ubuntu Puppy has a .pet {click to install} file for efax here:  [http://www.puppylinuxfaq.org/how-to9-add-on-software/pet/106.htm](http://www.puppylinuxfaq.org/how-to9-add-on-software/pet/106.htm)   Puppy is a nobrainer to setup for dialup and it flies on 256mb of ram and is fast on 128mb even on an ancient P3. You can also run it off a flashdrive as the laptop I am using now has no HDD. I love Ubuntu on my desktop with 2 gigs of ram but it will not run well on my lappie                                                                        rd

---

### Post by oldos2er on 2013-05-02
Old thread closed.

---

