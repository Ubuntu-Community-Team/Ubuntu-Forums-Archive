---
title: "Sony MP3 Player not being recognized"
date: 2008-05-08
forum: Hardware
---

### Post by darweth on 2008-05-08
Hello!

I have used a sweet Sony NWZ-A818 without problem or error on Gutsy Gibbon for months!  Since upgrading to Hardy Heron, I can no longer access it.  The USB slots are fine because I've plugged in external HDDs.  Also the Sony player itself shows a connection, just not Linux.  It used to pop up as an external drive that I could drag and drop my music collection onto but now NOTHING happens.  Any thoughts, my friends?

Thank you!

---

### Post by Canterwood on 2008-05-08
Maybe you should try installing Gnomad. It did the trick for my Samsung. Though I have a little experience with Sony and their Connect software, and to say the least: It sucks. However, if it worked under Gutsy, there should be a solution.

My Samsung was also recognized as a mountable drive, even though it's a U3-machine. A standard that hasn't been widely accepted yet. It wouldn't work no matter how I tried. Untill I installed Gnomad, it worked like a charm and now I'm happily transferring and arranging music. Give it a shot.

---

### Post by darweth on 2008-05-08
Hrm.  Is that a package?  apt-get says not.  I should probably open up Synaptic, heh.

---

### Post by Canterwood on 2008-05-08
It was a package for Dapper, but I don't know if it's been updated yet. It's a great player, and it's pretty widely used, so I'd think so. Check synaptic for your distro.

---

### Post by Canterwood on 2008-05-08
Oh, and if it isn't, I Googled it and here's how to compile it (in Dutch).

[http://nicdm.blogspot.com/2006/11/kleine-howto-voor-de-installatie-van.html](http://nicdm.blogspot.com/2006/11/kleine-howto-voor-de-installatie-van.html)

That probably isn't much help, so go to this link for the source packages:
[http://sourceforge.net/project/showfiles.php?group_id=65573](http://sourceforge.net/project/showfiles.php?group_id=65573)

Install some dependancies, the following:
sudo apt-get install build-essential libnjb-dev libmtp-dev libid3tag0-dev libglib2.0-dev libgtk2.0-dev libxml-perl checkinstall

Make a dir for the installation files: mkdir gnome_install
Go to the folder and extract the files to it, and then build from source with:

./configure
make
sudo make install

---

### Post by Canterwood on 2008-05-08
Sorry, double post.

---

### Post by darweth on 2008-05-09
Heyy!!  thank you!!  I found somethings out

1) the new version of Gnome supposedly has GIO issues with external devices so things could be messy.  Gutsy used an older GIO that was fine.  KDE's KIO detects my Sony fine.

2) Gnomad2 worked fine, but also AMAROK worked too!!!!  So I am set with Amarok! :)  It didn't work on Gutsy with Amarok but does now.  I guess libmtp was updated to support my Sony? Who knows!

Thanks.

---

### Post by diogui on 2008-08-27
Hi ! 

I just bought today a same sony model and I have the same problems with Ubuntu 8.04. 
I 've installed the gnomad2, so I can transfer music using that program. But I can use amarok to transfer songs, because it doesn recognize that the mp3 is plugged..I even can mount it manually. 

So could you tell me step by stpe how do you do it to make it work on amarok ?

Thanks and cheers

---

### Post by diogui on 2008-08-27
Yeaahhh I can use amarok ! The way I do it (it might be usefull for somebody):
In amarok > settings > media devices . I added a device names WALKMAN (not sure if the name is important but I think so) using MTP protocol . Ok and close it.

Then go to the Media Devices tab and you will see in the top a combo box with "MTP Device" click the button Connect and that's it :))

---

### Post by arvsr1988 on 2008-08-30
hey i have a sony NWZ-A829 and its not working on ubuntu... i can't even get it to mount manually although i can see it on my computer as an USB drive.

---

### Post by Marat89 on 2008-09-17
I just read that Banshee 1.2.1 has very goood support for devices in MPT Mode. Just try this, must be working

---

### Post by Interpreter on 2008-09-18
> **Marat89 said:**
> I just read that Banshee 1.2.1 has very goood support for devices in MPT Mode. Just try this, must be working

That would be perfect in my case, will report back once I get home.....10 hours that is. ))

---

### Post by bete on 2008-09-18
I baught the sony A826, and it does not show up as a folder, neither does amarok detect it, i tried adding it as a MTP media device in amarok, no go.
So im kinda helplpess here :(. Going for a trip tommorow and need some music on it.
No idea what banshee is, but i'll read up on it.

Btw, on my mp3 player screen it just says "connecting"

---

### Post by Marat89 on 2008-09-18
@bete
hi, i ordered today the same sony model ;-)
i Hope its going to work on Ubuntu
Please install Banshee and look after the support, maybe it is working, Im hope so for us all

---

### Post by bete on 2008-09-18
So i just installed banshee 1.2.1 and still no go :/.
Keep in mind i am a newbie in linux so i might not be doing things right. 
But seems to be a problem with the player + ubuntu itself, since the player doesnt show up in home folder. 
Just keeps trying to "connect".
The player looks and feels great tho ^^ so far im happy with it..

---

### Post by Marat89 on 2008-09-18
hi ok we have conversations on two threads, lets stay in this...
ok: have u tried gnomepad? rhythmbox??
to banshee: I read in the past that you have to add a hidden file in the root of some players, then banshee will be working in mtp fine..
EDIT:
I fine it out ;-). you must create only a hidden file in the root, named: .is_audio_player
But you cant save any file on it or?
so shows lsusb the player????

---

### Post by bete on 2008-09-18
I have not tried gnomepad and rhytmbox, but i dont think it will help as the player does not even appear as a folder in home :/.
Marat89, how can i add a hidden file if i cant even find the mp3 player :P..

---

### Post by Marat89 on 2008-09-18
go to Terminal and make :  hal-device | grep
add here the output
Information: [Banshee wiki]("http://wiki.banshee-project.org/Guide/DAPs/MassStorageDevices")
Best way: Can you join the IRC Channel of Banshee.?
irc.gnome.org
#banshee, im there too, you can find more helpers...

---

### Post by skintythe1andonly on 2008-09-18
Hi

I was having the same problems before when using linux mint (Ive now changed to ubuntu), the same thing really. Anyways I am using a NWZ-A816 and i found i couldnt mount it. pmount though seems to do the job. Once that is installed i have to run

```
ls /dev/disk/by-label -lah
```

at which i get something like

```
skint@skint-laptop ~ $ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2008-07-09 20:40 .
drwxr-xr-x 6 root root 120 2008-07-09 20:40 ..
lrwxrwxrwx 1 root root  10 2008-07-09 20:40 WALKMAN -> ../../sdb1

```

the thing is that sdb(whatever) is always changing.

To mount then all you have to do is 

```
pmount /dev/<device ID> SONY_WALKMAN
```

where <device ID> is replaced by the output ID from earlier (sdb1 or sdb2 or whatever) from earlier and you can now drag and drop files in

MTP works ok although I had some problems in Banshee before. I use Rhythmbox now but sometimes i want to store files on it like photos and stuff, which is when i need to pmount it. 

You will also need to use pmount to unmount it then

```
pumount SONY_WALKMAN
```

---

### Post by Marat89 on 2008-09-18
according to bete in banshee chat on irc your solution worked well. the only thing that dont work is the MTP Mode
how do you solve the banshee/mtp problem?
When you are using your player in MTP mode, have you to do the same pmount things, or is it gonna be connected automatic, have you a option on the player to change, USB/MTP

Could anyone post shell like code for the commands above, one for mount, one for unmount.
This could be some kind of solution, till LIBMTP adds these mp3 player series..

---

### Post by Interpreter on 2008-09-18
WOW skintythe1andonly it totally works and I love you, if this would be the RL id offer sexual favours and everything

Off, listening to some proper tuneage ))

---

### Post by Marat89 on 2008-09-18
cool, how is the banshee/mtp support, which sony player do you own?

---

### Post by skintythe1andonly on 2008-09-18
I never got it to work in Banshee which is actually why i changed to Rhythmbox. The mtp seems to work ok in this. 

This not automounting drove me mad too but it looked like it was a reported bug and is solved for Intrepid Ibex

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209483]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209483")

---

### Post by Interpreter on 2008-09-18
As for me it's a NWZ-A816,
I only use drag n drop for I hate using media player built in transfer things....

I also decided not to use banshee so I can't comment on that part ((.

---

### Post by Marat89 on 2008-09-19
ok, but hopefully there is a workaround for mounting (pmount) and the Banshee thing, i have to hack around, maybe i get it fixed, because the mtp is on rhythmbox working ;-) But thats not THAT problem.
Im waiting for Intrepid :popcorn::popcorn:

so thx to all, i report on Saturday if i Had luck with my new Sony nwz a826 :)

---

### Post by Marat89 on 2008-09-20
I have my nwz A826 :), its a great player and with pmount its working great ;-)
Banshee, Rhythmbox (MTP) do not work, Rhythmbox not tested.
I hope Intrepid will automatic mount this great player...
EDIT: actually you dont have to install and use pmount.
I just do: sudo mount /dev/sdb1
and sudo umoount /dev/sdb1

---

### Post by Marat89 on 2008-09-23
Push ;-)
has nobody a idea, how to get this player working with Banshee?

---

### Post by skintythe1andonly on 2008-09-24
Marat69, you dont have to use pmount but I found the command

```
ls /dev/disk/by-label -lah
```

doesnt work without pmount installed as the "by-label" part comes with pmount I believe. As for Banshee I gave up on it. Did turning off MTP in Banshee and then mounting it do anything?

---

### Post by Marat89 on 2008-09-27
> **skintythe1andonly said:**
> Marat69, you dont have to use pmount but I found the command

```
ls /dev/disk/by-label -lah
```

doesnt work without pmount installed as the "by-label" part comes with pmount I believe. As for Banshee I gave up on it. Did turning off MTP in Banshee and then mounting it do anything?

thx for the hint ;-). No, Banshee is not working with this player. I uses your method, but no chance:(

---

### Post by sithchikken on 2008-09-28
> 
Then go to the Media Devices tab and you will see in the top a combo box with "MTP Device" click the button Connect and that's it :))

Genius.   Worked perfectly, thanks.  

(8.04, 2.6.24-21-server)

---

### Post by Interpreter on 2008-10-29
Allight so ehm...
how's it working with Intrepid?
Someone here who knows this?

---

### Post by Interpreter on 2008-11-04
Wow, my walkman is now being recognized, though as a friggin picture device. As far as I know there's a big difference between mtp and ptp but hey, since I didn't buy supported hardware, neither did I write the code, I'm the one to blame for my own misery. Nah seriously. This Ibex has been pure fail so far for me.

---

### Post by skintythe1andonly on 2008-11-11
It is working fine for me now. it works just like a mounted drive..the way i want it. I am now on 64-bit intrepid though

---

### Post by sideswipe79 on 2009-01-01
I have a Sony NWZ-S639F that Intrepid 64 picks up a picture device while cleverly mounting to a mountpount WALKMAN... Anyway nothing sees it as a MTP device, not RhythmBox, Amorak or even using VirtualBox and a XP or Vista Virtual PC. They detect a MTP device but refuse to show it in the list of devices in WMP & the Sony Content Transfer software. 

Thankfully Amarok will happily mount it as an generic audio device and copy files onto it so not the end of the world by a long way.

---

