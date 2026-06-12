---
title: "Problems installing 8.04"
date: 2008-08-08
forum: General Help
---

### Post by Mike1227 on 2008-08-08
ok, i am a total newbie to linux I really dont know what i am doing yet. i have been running windows systems for ever and it is time for a change.
i'm trying to install ubuntu 8.04 and am hitting a brick wall!

System:
Dell GX150 Small Form Factor
1ghz p3
256mb 133 ram
30gig hdd
onboard audio sound and NIC

upon trying to install i insert the cd (downloaded from ubuntu.com and burned at 10x speed using NERO 7)

i get the ubuntu logo and a series of options (this is the alternative install because the live cd wouldnt work so i thought to give this a try)
I click "Install Ubuntu" and then I go to a blank screen with a blinking dash mark, no matter how long i wait nothing.

i have had this happen with another pc and with the live cd of 8.04 and the live cd of 7.04 this is really anoying!

i have seen posts of this exact pc running ubuntu no problem!
what am i doing wrong?????????

---

### Post by Sycron on 2008-08-08
What says that blinking dash ? something with busybox ?

---

### Post by snowpine on 2008-08-08
Simple problem, simple solution! You don't have enough ram (384mb required) to install using the live cd. But, you can download the Alternate Install CD, which should work with 256mb. There is also a distro called Xubuntu that works well on older computers. Good luck!

---

### Post by Ryadt on 2008-08-08
> **Mike1227 said:**
> ok, i am a total newbie to linux I really dont know what i am doing yet. i have been running windows systems for ever and it is time for a change.
i'm trying to install ubuntu 8.04 and am hitting a brick wall!

System:
Dell GX150 Small Form Factor
1ghz p3
256mb 133 ram
30gig hdd
onboard audio sound and NIC

upon trying to install i insert the cd (downloaded from ubuntu.com and burned at 10x speed using NERO 7)

i get the ubuntu logo and a series of options (this is the alternative install because the live cd wouldnt work so i thought to give this a try)
I click "Install Ubuntu" and then I go to a blank screen with a blinking dash mark, no matter how long i wait nothing.

i have had this happen with another pc and with the live cd of 8.04 and the live cd of 7.04 this is really anoying!

i have seen posts of this exact pc running ubuntu no problem!
what am i doing wrong?????????

You will have to install using the alternate cd. Download it from the Ubuntu homepage. Make sure you check the box where it gives you the option to choose for the alternate cd.
256 RAM is a bit tight to run Hardy anyway.

---

### Post by Sycron on 2008-08-08
Maybe it's not a good choice for him to handle a text based install ...

Download the alternate install CD and follow these simple steps:
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

Those that are on the right side.. Feel free to ask what it goes wrong.

---

### Post by Mike1227 on 2008-08-08
i am running the alternate install right now, do you think it still needs the extra ram?

---

### Post by Sycron on 2008-08-08
No. It is just fine. If you don't have enough ram ubuntu will use a swap drive. A swap drive is a partition used like RAM but it is SLOWLY ... but it's ok 256MB ram are enough...
follow these simple steps:
[http://developer.novell.com/wiki/ind...Install_Ubuntu]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu")

Those that are on the right side.. Feel free to ask what it goes wrong.

---

### Post by snowpine on 2008-08-08
> **Mike1227 said:**
> i am running the alternate install right now, do you think it still needs the extra ram?

256mb is the published minimum for the alternate cd ([http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)) so I think you should be able to install. Whether or not you will be happy with the performance once it's installed--that is another question! :)

---

### Post by Ryadt on 2008-08-08
> **Mike1227 said:**
> i am running the alternate install right now, do you think it still needs the extra ram?

It might be a bit buggy. But make sure you give it enough swap memory.

---

### Post by Mike1227 on 2008-08-08
i am still having the problem with the alternate install cd!
it wont do anything, it looks like its waiting for a command but i cant do a thing its been sitting 10 minutes and nothing.
what is wrongg?
i have some extra ram but its at my house, i will be there later and throw it in and bump it up to 512.

---

### Post by Sycron on 2008-08-08
Please explain what it's happening from the moment you boot up the CD...

---

### Post by snowpine on 2008-08-08
> **Mike1227 said:**
> i am still having the problem with the alternate install cd!
it wont do anything, it looks like its waiting for a command but i cant do a thing its been sitting 10 minutes and nothing.
what is wrongg?
i have some extra ram but its at my house, i will be there later and throw it in and bump it up to 512.

Be patient. It will probably take a few hours for the install to complete. Sometimes the progress bar will get stuck for 10-30 minutes; this is normal.

---

### Post by Ryadt on 2008-08-08
> **Mike1227 said:**
> i am still having the problem with the alternate install cd!
it wont do anything, it looks like its waiting for a command but i cant do a thing its been sitting 10 minutes and nothing.
what is wrongg?
i have some extra ram but its at my house, i will be there later and throw it in and bump it up to 512.

It not loading is not a problem with your RAM. Try checking your cd for errors.

---

### Post by Alfred_McGee on 2008-08-08
@ Mike1227:

When you switch on your computer, the Ubuntu CD should give you the option to test it and make sure it's OK. It's possible your hardware doesn't meet the requirements for Ubuntu 8.04, and would be better with some older software, but try booting (rather than installing) Ubuntu 8.04 from your install CD. Once booted up, there's an installer icon on the live CD desktop that you can click to begin installation to your hard drive. Alternatively, for older computers, Puppy linux is a great lightweight distro.

---

### Post by Sycron on 2008-08-08
> Alternatively, for older computers, Puppy linux is a great lightweight distro. 	

like **Zenwalk** or **!#CruchBang linux** that is a ubuntu with openbox and XFCE.

---

### Post by snowpine on 2008-08-08
> **Alfred_McGee said:**
> @ Mike1227:

When you switch on your computer, the Ubuntu CD should give you the option to test it and make sure it's OK. It's possible your hardware doesn't meet the requirements for Ubuntu 8.04, and would be better with some older software, but try booting (rather than installing) Ubuntu 8.04 from your install CD. Once booted up, there's an installer icon on the live CD desktop that you can click to begin installation to your hard drive. Alternatively, for older computers, Puppy linux is a great lightweight distro.

256mb of ram is not enough to install by clicking the install icon on the live cd desktop. And I would personally try Xubuntu before I tried Puppy, as Xubuntu and Ubuntu are about 90% the same--Puppy is a different (if wonderful) animal.

---

### Post by Mike1227 on 2008-08-08
im using the alternate cd. all it does is start up the cd with the big ubuntu logo ask for the language and ask what i want to do. i click "install linux" and it says loading kernel then goes to a blank screen and blinkng dash.

---

### Post by Sycron on 2008-08-08
:| it seems that your connection is very slow ... it happened to me when i was installing ubuntu on a USB 1.1 port.... VERY UNPLEASANT memories... kernel loaded after long long long time...

You are installing from a CD, right ? an IDE one ?

---

### Post by Ryadt on 2008-08-08
> **Mike1227 said:**
> im using the alternate cd. all it does is start up the cd with the big ubuntu logo ask for the language and ask what i want to do. i click "install linux" and it says loading kernel then goes to a blank screen and blinkng dash.

Check the cd for any errors.

---

### Post by Mike1227 on 2008-08-08
i am loading from a cd (it is ide but it is a small form factor so it uses a laptop cd rom and i would guess it is SLLLOOOOWWWW
the busy light stops after a while though and i dont know if it is still working.....
is it normal durring install to see the blank screen with the dash?

---

### Post by Sycron on 2008-08-08
> Check the cd for any errors. 	

Do this... i almost forgot .. one day i couldn't install ubuntu from my CD-RW because the CD-RW was dirty .. and I have to clean it an reburn again...

---

### Post by Mike1227 on 2008-08-08
it wont even run the cd check for errors! it goes to the blank screen with the dash also...
i downloaded 7.04 yesterday and that did the same thing.
what is going on here???

---

### Post by grimrider on 2008-08-08
try hitting F5 (?) to bring the more options menu up and type "linux acpi=off".  thats how i got mine to boot a while back.


EDIT:  F6 my bad

---

### Post by Sycron on 2008-08-08
> i am loading from a cd (it is ide but it is a small form factor so it uses a laptop cd rom and i would guess it is SLLLOOOOWWWW
the busy light stops after a while though and i dont know if it is still working.....
is it normal durring install to see the blank screen with the dash?

as far as i know all alternate CD's are text based install with blue background like in this tut [http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

---

### Post by Ryadt on 2008-08-08
> **Mike1227 said:**
> it wont even run the cd check for errors! it goes to the blank screen with the dash also...
i downloaded 7.04 yesterday and that did the same thing.
what is going on here???

There most probably is a problem with the cd. Anyway try checking the md5sum
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Mike1227 on 2008-08-08
i just ran the cd on another pc with a regular cd rom drive and it started no problem!
i think i will try using a normal cd rom drive for install

---

### Post by Sycron on 2008-08-08
> think i will try using a normal cd rom drive for install 	

Now are you using an anormal CD drive ? :) joking...

---

### Post by Mike1227 on 2008-08-08
well, it still isnt doing anything i am using a regular non-laptop cd rom drive and it is sitting there. the cd was checked on another pc and is good. is there a problem i am not seeing? 
do i need a driver to install this? hhhmmmmmm
can i install this using another pc and install the hard drive in this system?

---

### Post by Sycron on 2008-08-08
> can i install this using another pc and install the hard drive in this system? 	

Yes i've done that and it works just fine on every computer...

---

### Post by snowpine on 2008-08-08
Mike, ubuntuforums is the best resource on the 'net, so if it is possible to install Ubuntu on that computer, we will help you do it! What you have to remember is that your computer is at the absolute bottom end of Ubuntu's system requirements. There are other distros (Xubuntu is just one example) that are better suited for lower-spec machines. But we love to push the boundaries, so if we can help you squeeze Ubuntu in there.... :)

---

### Post by Sycron on 2008-08-08
I'm going to sleep now so don't be sad if I won't answer you anymore...

---

### Post by Mike1227 on 2008-08-08
i have a 1.0ghz processor.
with 512 ram will all of this go away? hahaha
i tried install on another pc in the house and it is a gx150 with a 1.0ghz p3 with 512 ram. what is the real difference????
if i install my extra memory to bump it up to 512 with it go through with the install?

---

### Post by Sycron on 2008-08-08
Yes, but it doesn't seem to be a RAM problem...
Good night mike.

---

### Post by Mike1227 on 2008-08-08
i know for a fact this machine will go through with a windows xp install no problem (well it did last year........)
what else could be wrong?

---

### Post by snowpine on 2008-08-08
Mike, give this thread a read: [http://ubuntuforums.org/showthread.php?t=759610&highlight=GX150](http://ubuntuforums.org/showthread.php?t=759610&highlight=GX150)

And yes, generally speaking, going from 256 to 512mb makes a huge difference with Ubuntu.

---

### Post by snowpine on 2008-08-08
And another one: [http://ubuntuforums.org/showthread.php?t=664725&highlight=GX150](http://ubuntuforums.org/showthread.php?t=664725&highlight=GX150)

Sounds like it is a video problem, not a ram problem.

---

### Post by Sycron on 2008-08-08
> And yes, generally speaking, going from 256 to 512mb makes a huge difference with Ubuntu.

It really does since I was in that situation..

---

### Post by Mike1227 on 2008-08-08
i am going to update the bios and give it another try.
i dont have any video options in my bios and updating might get me to a point where i can select more vid ram (maybe im using   
1mb lol)

---

### Post by grimrider on 2008-08-08
did u try disabling acpi?  my computer did the same thing

---

### Post by Mike1227 on 2008-08-08
nevermind i am using the latest bios hahaha

---

### Post by Mike1227 on 2008-08-08
i tried i dont know if i did it correctly i hit f6 and typed "noacpi" then i tried "acpi=off" after typing that do i hit something other than enter?

---

### Post by grimrider on 2008-08-08
no that should have worked.  idk if it makes a difference but i typed "linux acpi=off"

---

