---
title: "Ubuntu Powered Carputer"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by iamdigitalman on 2007-08-01
Hey, this is a project I have been thinking about doing for some time. My original plan was to get a Libretto 1xx, but those were too expensive. Then I realised there was a 50M with a touchscreen. Too rare and expensive again.

So, I looked around, and I found some slate style older tablets, running Windows 98. I decided on a touchscreen so I could use some sort of front end to operate all the functions. at first I wanted something with 2 serial ports, which is kind of a luxury without resorting to a dock on a portable machine. I have now changed my tune, and I'd like something with in built USB (does not have to be 2.0.) I can actually get away with a single port machine, and use a 4 port hub. That would make it easier to just unplug a single USB device (the hub), and remove the carputer, for security reasons, as well as being able to use it as a portable machine in the field.

So, I was wondering if Ubuntu has built in tablet support, or some extra software I can use, or am I going to have to resort to Windows XP Tablet PC edition 2005 (just saying that makes me feel sick.) I also need drivers/software for some other functions of the carputer:

-ODB-II diagnostic software
-GPS navigation software
-webcam support (going to use it as a backup camera)
-Support for a 3G/wifi combo PCMCIA card for internet access (from AT&T/Cingular, specifically).
-a media front end of some sort, that is fully programable (like the now defunct road runner)

so, any thoughts? I REALLY don't want to use Xp, but if I end up doing so, i'll skin it like some other OS we all love.

-digital ;)

---

### Post by iamdigitalman on 2007-08-09
Ok, well I found a topic on here on getting the tablet portion working on a Fujustu Stylistic 3400/3500. It's a serial device, so it should work on others as well. I may even end up getting an old stylistic 1000 or 1200 with the black and white screen, because I won't be displaying video, and color screens tend to wash out in the sun. But, then again, I kinda want built in USB.

Now I just need to get a front end for it. I may just code something in java or Flash. I set that to run at login, and it should be good.

As for GPS navigation, I was thinking MS streets and trips. I could use wine to run it. I hate MS products, but the voice turn by turn is so slick.

I also forgot webcam support could be added really easy, or is it built in? I don't remember.

Now all I need to solve is the 3G card, and ODB-II software. I think I could use NDISwrapper on the 3G card, or would that not work?

so, i'll keep you guys updated on the status of the project, and i'll let you know if I end up with something ubuntu powered or not. 

I also found out that WXPTPCE2K5V2K2SP2 (even for an acronym, that is a mouthful), won't even work with the built in stuff. It turns out it only supports 'active digitizers' and the ones on the older stylistics are passive, which is unsupported.

-digital ;)

---

### Post by jai_mantravadi on 2007-10-07
Navit and Roadnav are open-source GPS software. Basically only useful in the US. If you're looking for a commercial solution but hate microsoft, apparently iGuidance "just works" under linux if installed with crossover office (not wine). I've never tested any of these as I haven't built my car computer yet. I'm leaning towards iGuidance myself. 

Check out:
[https://www.timekiller.org/carpc/software.php](https://www.timekiller.org/carpc/software.php)
[http://gentoo-wiki.com/HOWTO_Car_Computer](http://gentoo-wiki.com/HOWTO_Car_Computer)

Post back if you're able to get any of the options to work! 
Good Luck
Jai

---

### Post by Doofguru on 2008-05-15
Hi iamdigitalman

i am actually trying to do almost the same thing, tho my car was in an accident recently so i haven't been doing much to the project. how are you going with the software? im am having some trouble with Navit tho i haven't spent much time on getting that going either.

if you find any good front end software i would love to know about it.

---

### Post by iamdigitalman on 2008-05-15
oh wow, I totally forgot about this whole idea. End of last year and beginning of this one were crazy. Now that the weather is warming up, I may want to try it again. I still think a stylistic is the way to go, but instead of using the full bore ubuntu, I might go for one of the stripped down varriants, because if I were to get solid state storage, every last inch of space would need to be accounted for.

I will see what I can do when I get some money in.

-digital ;)

---

### Post by Doofguru on 2008-05-16
if your worried about startup times i was thinking about just getting a 4GB flash drive or some compact flash thing up and going, install linux onto that and then use the laptop hard drive for storage. shouldn't cost to much, I'm in Australia and down here you can geta 4GB Corsair flash drive 19Mb Read and 13Mb write speeds for $55Aud good enough to boot off. And once you have the OS started you shouldn't really need fast read write times. especially if it's only going to be doing gps mp3's and smaller things like that. 

I installed a command line ubuntu 8.04 install and then manually install xorg and gnome and so on, then i don't have all that other crap like openoffice, evolution and gimp like you get when you install ubuntu normally.

i have a E36 BMW here is what i want to do

Reverse camera
GPS (hopefully with navit and openstreetmap)
a run of the mill mp3 player
dvd player
security coded engine start (should be easy to do just need a relay switch controlled by the laptop)
and i would like to use my phone through it as well but i dont think that will happen.

im working on the gps atm trying to get it to work, i have navit installed but as per my previous post i haven't spent much time on it. the reverse camera will be easy tho im not sure how i will make it come up when reverse is selected.

would be good if you got back into the project.

Doofguru

---

### Post by iamdigitalman on 2008-05-24
Alright, I am all fired up to do this project now. I just bought a 3500 on ebay. Specs are modest, but it should be able to run some form of ubuntu. Here is what it has:

-Intel celeron 500mhz ultra low voltage processor
-64mb (!) of RAM
-6gb mechanical hard drive
-Windows 98 installed
-Comes with an 802.11b wifi card
-comes with a mini dock port replicator

64mb is way too little RAM for my liking. If it takes PC100 like I think it does, I have some 128mb sticks. I read the maximum this machine can take is 256mb, and that is below the minimum system requirements to run ubuntu.

I think I am screwed here, but if it comes to I can't run it, I will just stick windows 2k on it. I have some larger spare mechanical hard drives, but the ideal situation would be a compact flash card, 8gb or 16gb, in an IDE to CF adapter.

-digital ;)

---

### Post by priegog on 2008-05-24
by 3500 you mean a stylistic 3500? Whathever the case, I think in any way the normal vanilla ubuntu wouldn't be appropiate for a carputer. You have xubuntu and fluxbuntu and whatnot...Maybe even none of those; as the ideal setting would be a big, pretty frontend a-la mythtv. I just an old tablet with ubuntu... not exactly for this purpose, tho, but I did manage to setup the gps apps and they work great. Let us know how your progress goes. 
Oh, one more thing... maybe when they release ubuntu mobile that could suit you. It would have to be hacked into it as I believe it's been created for the purpose of intel MID's but whatever... this is linux right? I think I read somewhere they were going to release it shortly after the release of Hardy , so...

---

