---
title: "How to sync music iPhone 4 and ipod touch 4g (ios 4.2.1"
date: 2011-04-16
forum: Hardware
---

### Post by sudsiv on 2011-04-16
1. Jailbreak and download ifile
2. Go to system/library/lockdown/checkpoint.xml
3. Edit the file so that the value dbversion is 4
4. Go to var/mobile/media an delete the itunes control folder
5. Reboot the device
6. Connect to itunes(you need a windows comp or mac) and add 
a song to initialize your device

Now prepare your computer:

Open up synaptic (system->synaptic pacage manager
2. Go to the Repositories (Under Settings)
3. Add this source:
[noparse]ppa:pmcenery/ppa[/noparse]
4. Close and click reload
5. Search for libimobiledevice1 and install both
6. Now close synaptic open terminal and type:
sudo apt-get dist-upgrade

 You can now connect your device to your Computer and sync with rhythmbox or banshee

note: tested with ubuntu 10.10 maverick

---

### Post by volto on 2011-06-16
Thanks alot man, Finally got my iphone 4 to sync using banshee thanks to your instructions :).

Confirmed to be working on iPhone4 4.2.1 and Ubuntu 11.04 Natty

---

### Post by deltacomp on 2011-07-08
Amazing, it works! The only problem I ran into was after the music was on there, all the apps that were added after-market would not stay open, this was easily fixed by deleting an app (pandora) and reinstalling it through the app store. After that, everything worked perfectly!

Thanks!!!

---

### Post by jandresfg on 2011-07-12
There's still something I dont get... when I plug the ipod to itunes in Windows it asks me to configure the ipod before adding any song, wich creates again the iTunes control folder.... how can I avoid that??

---

### Post by deltacomp on 2011-07-13
> **jandresfg said:**
> There's still something I dont get... when I plug the ipod to itunes in Windows it asks me to configure the ipod before adding any song, wich creates again the iTunes control folder.... how can I avoid that??
 
 
All I did was plug in my iphone to and synced a song. Once I did that I was able to use Banshee to add the other songs. If itunes is telling you to create a new profile for your phone, either cancel it if you can or just follow through the process and contiue with Banshee.

---

### Post by jandresfg on 2011-07-13
> **deltacomp said:**
> All I did was plug in my iphone to and synced a song. Once I did that I was able to use Banshee to add the other songs. If itunes is telling you to create a new profile for your phone, either cancel it if you can or just follow through the process and contiue with Banshee.
itunes doesn't let me sync any song without configuring it, and there's not any cancel option either. After creating the profile (I've tryed both as a new ipod or setting the last backup) the iTunes Control folder is created again.... I'm stucked :/

---

### Post by luisloboborobia on 2011-08-09
I'm new to iPod (have a Touch 4G).

Is it a Must to jailbreakit to allown music sync in Ubuntu?

---

### Post by deltacomp on 2011-08-09
Hello, yes you must jailbrake your phone. Once iTunes has started to sync your phone just let it finish. When it's done add a song to your iPhone then go back into Banshee and you will be able to add/sync songs. If you still can't get it to work I'll try to be more specific when I have more time.

---

### Post by digitalramble on 2011-12-09
OK, I'm bumping this.

Currently, I have Ubuntu 11.04, with all the latest updates.  I have Banshee 2.0 installed.  I have an iphone 4G, with iOS 4 (the one just before 5).

Now, banshee can see my iphone, and when I created a playlist and dropped it on the iphone, it went through all the motions.  And when I check my iphone, the disk usage drops the same amount (that is, I put 1G of music up, and iphone now shows 1G additional disk usage.  But the ipod player doesn't recognize that any music has been loaded!

Do I have to do the jailbreak thing for this as well?  I really want to be as lazy as possible in setting this up.  (Eg, if it's easier to just export everything from banshee to rhythmbox and go from there, then say so and I'll do that.)  Or did I overlook something simple?  If 11.10 fixes this issue, I can upgrade (I plan to do so in the next month or so anyway).

Meh.  Was going to try syncing from sugarsync since iphone doens't deal with Amazon cloud, only to find that sugarsync doesn't have a robust app to work with Linux *headdesk*

---

### Post by jdorenbush on 2011-12-22
> **digitalramble said:**
> Currently, I have Ubuntu 11.04, with all the latest updates.  I have Banshee 2.0 installed.  I have an iphone 4G, with iOS 4 (the one just before 5).

Now, banshee can see my iphone, and when I created a playlist and dropped it on the iphone, it went through all the motions.  And when I check my iphone, the disk usage drops the same amount (that is, I put 1G of music up, and iphone now shows 1G additional disk usage.  But the ipod player doesn't recognize that any music has been loaded!

I think I'm experiencing the same problem as *digitalramble*. In the past, I could add music to my iPhone via Banshee, but now after I add music to my device through Banshee it disappears after I open up the iPod app on my iPhone.

I assume that the latest Apple OS update is at fault for this problem, as I only started experiencing this issue after I updated my iPhone.

_System/Device Details_
- iPhone 3GS - Version 5.0.1
- Ubuntu 11.04 64bit
- Banshee 2.3.2

---

### Post by GrouchyGaijin on 2011-12-24
> **jdorenbush said:**
> I think I'm experiencing the same problem as *digitalramble*. In the past, I could add music to my iPhone via Banshee, but now after I add music to my device through Banshee it disappears after I open up the iPod app on my iPhone.

I assume that the latest Apple OS update is at fault for this problem, as I only started experiencing this issue after I updated my iPhone.

_System/Device Details_
- iPhone 3GS - Version 5.0.1
- Ubuntu 11.04 64bit
- Banshee 2.3.2

Same problem

---

### Post by lasleym on 2012-01-10
I have an iPhone 4S and Ubuntu 11.10 (using Unity). I found this response to be helpful for deleting the "hidden" files. 
[INDENT]There may or may not be a couple of ways of doing this.
  First off you could use nautilus to navigate your iphone into the /iTunes_Control/Music/ folder. There you should find folders named Fxx. When inspecting these folders you should try to find files named lipgodxxxxxx as opposed to the iTunes synched files which should be named with 4 capital letters.
  The lipgodxxxxxx files are the ones uploaded onto the phone via banshee.
  Once you're at this step and you've asserted that this is indeed the  case you can either browse all folders and remove them manually or use  the following command:
  find ~/.gvfs/XXXXX/iTunes_Control/Music -name "libgpod*" -exec rm -f {} \;   Where XXXXX is the device's name (as it shows in the nautilus sidebar)
[/INDENT][http://askubuntu.com/questions/90039/ios5-banshee-and-memories-gone](http://askubuntu.com/questions/90039/ios5-banshee-and-memories-gone)


I did not use the find command, as each folder (FXXX) had the "lipgodxxx" file in it. I think my Banshee tried to delete and sync so many times, I ended up with 13GB of data I couldn't use or see until I followed these instructions. At least I've been able to delete without visiting the Apple Store. 



I still can't figure out how to sync properly using Ubuntu (Rythmbox keeps crashing or Banshee). I'll resync at work where I use a PC with Windows 7 and the latest iTunes.

---

### Post by dahumph on 2012-03-13
> **sudsiv said:**
> 1. Jailbreak and download ifile
2. Go to system/library/lockdown/checkpoint.xml
3. Edit the file so that the value dbversion is 4
4. Go to var/mobile/media an delete the itunes control folder
5. Reboot the device
6. Connect to itunes(you need a windows comp or mac) and add 
a song to initialize your device


As far as I know this was the only way to sync the iphone 4 using ubuntu. Anyone tried that with iOS 5? Is it still working with this modifications? I'm still using iOS 4.1, want to update, but dont want to lose the sync with ubuntu....

---

### Post by pholorian on 2013-01-04
I installed ezmp3 from the app store (free or €1.79 pro version without ads).  I then connected my iPhone 4s (IOS 6.0.1) to my linux box (Ubuntu 12.04 64 bit) via USB  and when the list of files on the iPhone opened in Nautilus I doubled clicked on the exmp3 icon to open that apps Documents folder.  I then dragged folders containing mp3 files from ~/Music/  into the open ezmp3/Documents folder.  The app will then play them using 'folder play'.  Ensure your music folders are only nested 1 deep so the path to any mp3 is ezmp3/Documents/folder_name/ tune_name.mp3..  Nautilus doesn't refresh the iPhone window automatically, so you need to do this is you wish to follow your progress.  I know it is a drag n drop rather than a sync, but it worked fine for me.

---

### Post by antigaston on 2013-02-18
[[COLOR=#000000]pholorian[/COLOR]]("http://ubuntuforums.org/member.php?u=657372") i bought the ezmp3 app and i can succesfully drag the mp3's to the document folder and play them. But i can't use the iPod libarary in the app, does it only work with music you have synced with Itunes? I hope not.. Hope you can help :)

---

