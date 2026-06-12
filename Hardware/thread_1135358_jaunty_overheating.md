---
title: "jaunty overheating?"
date: 2009-04-24
forum: Hardware
---

### Post by erqiyang on 2009-04-24
I've just performed a clean install for my HP Pavilion dv2000 with 9.04 . Problem is, after installation, my harddisk got really really hot. It seems like there is unusually high amount of read/write.

Just wondering, if anyone else is having this problem too? And if there is any solution for it?

Btw, I am using ext4.

---

### Post by gertpozzo on 2009-04-24
The same thing happened to me, with an XPS 1530. The PC became so hot that it shutdown itself. However now it works well.

---

### Post by dE_logics on 2009-04-24
You can report a bug about this.

---

### Post by erqiyang on 2009-04-24
Pardon me for being new, but how should I report it?

---

### Post by adrian.tuhut on 2009-05-08
this behavior is not a bug......trackerd daemon is indexing your files and that is why you see intense hdd activity...

---

### Post by Marvin666 on 2009-05-08
Is there a way you disable this indexing service, or is it needed for something in ubuntu?

---

### Post by alexandari on 2009-05-08
yeah go to **Menu System> Preferences> Indexing Preferences **
then uncheck **"Enable indexing" and "Enable watching"**
I rly don`t know how much will this help but...I mean it didnt help me

---

### Post by NilsE on 2009-05-08
I have noticed that trackerd daemon is indexing your files and will seem to be all the time but it actually stops being so intense after the first few boots when it finishes it's initial indexing.  Then it is minimal.

So, that could be causing the drive to heat up but should settle down soon.  If it does not then by all means shut of trackerd.  The only problem that causes is a little slower searches but in my opinion it was minimal when I shut it off when I was on 8.10.

---

### Post by Marvin666 on 2009-05-08
I don't have the above option in my menu. I'm running xubuntu.

---

### Post by gianluca.pettinello on 2009-05-10
I have a dv2000 laptop with ubuntu 9.04 ext 4 installed too and I noticed, after some upgrading that the hd is overheating. I don't have tracker enabled. Besides my battery lasts 1 hour or a bit more. It is frustrating !!:confused:

---

### Post by dsiddens on 2009-05-13
HP d8000 AMD64 here.
According to System Monitor Processes, trackerd is consuming between 0 and 1 % on my system.  (I have it set low.)

I do not believe this overheating is caused by tracker, dust in the cooling circuit, intense video applications...

This machine did not over heat with Intrepid.

Doug

---

### Post by junalmeida on 2009-05-17
After upgrading here from Intrepid to Jaunty, my tx2110 goes over 90oC and shuts down when i'm using some application that needs intense processor activity. 

Everything works fine on Intrepid with the same applications...

---

### Post by salamay on 2009-05-18
I had this crazy overheating issue when i upgraded from intrepid to jaunty.
After spending so much time i figured that google gadgets (ggl-gtk) was using 50% of the cpu continuously. After quitting ggl-gtk - temps dropped from 85C to 45C. whooooops! what a relief.
you might try doing so if you have ggl-gtk running.

---

### Post by skintythe1andonly on 2009-05-28
i have noticed my temperature to have risen too with my upgrate. I am also using a dv2000. I initially thought it was the GPU (nvidia geforce 6150 go) but now suspecting the hdd. battery time is down too

---

### Post by ssri on 2009-05-28
> **junalmeida said:**
> After upgrading here from Intrepid to Jaunty, my tx2110 goes over 90oC and shuts down when i'm using some application that needs intense processor activity. 

Everything works fine on Intrepid with the same applications...

Fire up the terminal and..

~$top

See which programs are hogging your CPU.

---

### Post by spiceminesofkessel on 2009-05-28
I have a PowerBook G4 1.0GHz running Jaunty PPC edition that does the same thing. I unpacked an archive file and it shut down in a hurry. I nearly burned my hand when I touched the bottom of the laptop.

---

### Post by skintythe1andonly on 2009-05-29
when I run hddtemp, it says that there is no temperature sensor for my hard drive. Is this the case for anybody else here specifically the ones with the hp laptops?

or is this a ext4 problem?

---

### Post by skintythe1andonly on 2009-05-29
So I have done some looking around and contrary to what hddtemp is saying about my hard drive not having a temperature sensor, my hard drive does according to [http://www.almico.com/forumharddisks.php?man=65]("http://www.almico.com/forumharddisks.php?man=65")

This may be the problem, is hddtemp working for anyone else?

---

### Post by jimblandy on 2009-06-01
I found that running compat-wireless (as suggested on the [Intrepid MacBook Pro 3.1 page]("http://help.ubuntu.com/community/MacBookPro3-1/Intrepid"), say) caused my laptop to run hot, and occasionally freeze.  As I said on that page:

You should be aware that bleeding-edge kernel code hasn't had much testing, and bugs in it can do almost arbitrarily bad things to your system [...].   Try it if you like, but suspect your riskiest move first if troubles arise.

---

### Post by abhiroopb on 2009-06-02
My laptop (HP DV5242ea) kept switching off with and I wasn't sure why. It turns out my HD temp kept rising to about 60C!!! And this is beyond the standard operating temp. I have a WDC WD3200BEVT hard drive.

It has only started overheating recently. Does anyone have any tips? My CPU usage does not seem unusually high. Any suggestions?

---

### Post by pamazon on 2009-06-03
I have two different laptops overheating on jaunty. I had no problems with intrepid or fiesty on the same machines. I can boot into windows and they stays cool. 

It gets hot enough to burn even when the labtop is closed.

They are ext3 installs.

Has anyone had any success or do I have to downgrade? That would be so annoying.

there is a bug reported, but it's incomplete.
[https://bugs.launchpad.net/bugs/375285](https://bugs.launchpad.net/bugs/375285)

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---

