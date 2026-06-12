---
title: "help please"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by hoha7 on 2009-02-14
i got my ubuntu cd and startd installing it but it would hang after the orange bar moves to and fro and it starts loading (at about 18%)..

i tried alternate install ..it was succesfull but ubuntu took a lot of timee to start up and then after ntering my username and pass it would freeze
my pc is above the requirements needed for ubuntu to run

help me!!!!!!!:sad:

---

### Post by x33a on 2009-02-14
first,check the md5 checksum of the downloaded iso. the, try burning a new disc at low speed. after the burn is complete, again check the disc for any errors. then proceed with the installation.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by hoha7 on 2009-02-14
there ar no errors on the cd ,i burned it at the lowest speed possible(8x) on the cd and checked the md5 checksum of iso but still no gud

---

### Post by binarypill on 2009-02-14
when you insert the CD, use the "check CD for defects" function. it will take some time but this ensures that you're installing from a good burn. 

if you have a bad install, you probably just have to reinstall. in my experience, a good ubuntu install is one when you can actually get into the "live cd" session of ubuntu. this way, you are assured that your hardware can handle ubuntu.

---

### Post by hoha7 on 2009-02-14
btw i got this cd(normal ubuntu) from shipit so it must be fine and i have chcked it nd no errors and again geet stuck on the orange bar thing and the cd sounds like it has stoped roating

---

### Post by linux_tech on 2009-02-14
If you have trouble installing from the live cd, then give the alternate cd a try

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by hoha7 on 2009-02-14
i had tried it too and it worked fine but when ubuntu starts to load it takes 10 mins and thn ftr entering pass and username it freezes

---

### Post by x33a on 2009-02-14
if you are absolutely sure that the cd is fine, then there might be a problem with your hardware.

check the hard drive for defects using a bootable disc like system rescue disc. or if you are dual booting, run chkdsk and/or other hard drive utility.

---

### Post by hoha7 on 2009-02-14
k i did the check disc and it the same prob during install
but i waited long n some screen comes up where infront of everything comes permission denied and in the last "eexecution of /bin /(something like sh) failed"

---

### Post by x33a on 2009-02-15
so did you manage to install? if you didn't i think you should download ubuntu iso from the net and then use that. (assuming you are using the shipit version).

---

### Post by yeats on 2009-02-15
sounds like a bad CD rom drive to me, having lived through that same situation.  If your main goal is getting Ubuntu installed, you should download a fresh image of the alternate CD and install that way.  If that doesn't work you should look into either replacing the CD ROM or using alternate installation methods.  (IMHO)

---

### Post by theozzlives on 2009-02-15
I'd try memtest +86... sounds like a memory problem to me

---

### Post by hoha7 on 2009-02-15
okay ill try to download the version and will post the results tomm...(i have already tried the alternate install)

---

### Post by hoha7 on 2009-02-15
n ill try memtest +86 too

---

### Post by hoha7 on 2009-02-16
downloaded the ubuntu image and wrote to cd (lowest speed) and tried mem test (no problems) but still no gud............

---

### Post by x33a on 2009-02-16
test your hard-drive for defects.

---

### Post by lswest on 2009-02-16
If your computer supports booting from USB and you have a 1GB USB stick, you can use [UNetBootin]("http://sourceforge.net/projects/unetbootin/") to "burn" the CD image to the USB to circumvent the CDRom drive (if that is indeed the problem).  I'd give it a shot.

---

### Post by hoha7 on 2009-02-16
i will try wht lswest has said ......

---

