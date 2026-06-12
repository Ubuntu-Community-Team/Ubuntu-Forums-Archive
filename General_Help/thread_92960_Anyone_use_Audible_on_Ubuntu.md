---
title: "Anyone use Audible on Ubuntu?"
date: 2005-11-20
forum: General Help
---

### Post by meta87 on 2005-11-20
I am loving Ubuntu and have recently stopped using windows entirely. The only thing still bothering me is my Audible audio books. I installed audible manager via Wine and it runs fine, but I can't download my audio books! 

The problem is that audible.com sends a small .pl file that the software audible manager opens and then downloads the audio book file. I can't seem to get firefox to send the file to audible manager. 

If anyone has this working or knows another way I could do this that would be great! Thanks alot everyone. :)

---

### Post by murkin on 2006-01-17
Has no one found a way to play .AA / Audible files on Ubuntu or is WINE the way to go?

---

### Post by vbt on 2006-08-22
I wrote customer service and only got a "sorry won't work on linux" answer. The only way I was able to download my books was to install their manager through wine, along with itunes and ie6. 

If anybody has another suggestion, I'd like to know. Still new to linux.

---

### Post by zami on 2006-08-29
I'd love to know of an easier way to do this as well.

I've got the manager installed, but it looks all skwonky (text piled up, buttons over the wrong text, etc), I can't "activate" it as a player, and I can't download any book files anymore.

I'm trying the iTunes/IE/iTunes-manager route, but can't get iTunes to install.  Still working on that.  Just seems to hang during installation.

Anyone know of a solid alternative to Audible altogether?  Aside from being trixy to install in a Linux box, they've gotten rather spendy over the years, too!

-zami

---

### Post by CAD-MAN on 2007-08-27
So it looks like I'm, erm, a year late for this topic! Just thought I'd bump this existing one instead of posting my new topic.

So, any news on this little snag? Is WINE still the only way to go?

Cheers

---

### Post by CAD-MAN on 2007-08-28
Anyone....:confused:

---

### Post by BigSilly on 2007-09-14
Computer says.....no.

/COUGH

The missus decided last night she would boot into Windows and download an audiobook from Audible. She's never done it before, but really wanted this thing and it was at a good price. I've never used anything like Audible myself before, so I watched her process. After a bit of faffing, she got the audio file she wanted, which Audible stuck directly onto her MP3 player (a fairly generic Sansa thing). When she'd done, she said I could copy the file if I wanted, since I have exactly the same player.

It wasn't having *that!*

I booted into Ubuntu and mounted the NTFS partition, and I then copied the file into my spare FAT32 partition (since it wouldn't allow such manipulation from XP) just for safe keeping until I get a solution to this.

So, I'm hoping someone can help here with regards a Linux solution to this little problem. I just want to convert the thing to MP3 so I can listen to it on my own player. Is there no way to do this using Linux then?

---

### Post by puppy on 2007-09-27
That's cos the file is DRM'd - you're going to have to rip out the copy protection from the file before you can use it. And if you're in the UK that is *not* illegal, it's your file, you bought it, and you can make any 'reasonable' use of it that you want. 

Tbh because of the way they have no time for linux users, their pricing structure and DRM , my personal view is that Audible can go take a running jump as far as I'm concerned - I think I'll go read a paperback book instead... :mad:

---

### Post by zami on 2007-09-27
> **puppy said:**
> ...And if you're in the UK that is *not* illegal, it's your file, you bought it, and you can make any 'reasonable' use of it that you want. ...

I'm jealous!

I might actually just move to Simply Audiobooks or some other Netflix style "books on CD" service.  Audible used to be two BOOKS a month for the base subscription - now it's two CREDITS a month, and sometimes a single book costs many credits.  Definitely not the same service I subscribed to years ago.  And a few WINE updates later, I still can't get their audible player to perform correctly. (Nor in Crossover, nor (heavens help me!) Cedega.)

Oooh.. .I've got ReactOS (windows architecture OS) running in Virtualbox (emulator) mabye I'll try that... I'm not holding my breath but if I'm pleasantly surprised I'll leave an update.

-zami

---

### Post by lavs23 on 2007-11-02
Unfortunately the only way I've found to use Audible is using a VirtualBoxed Windows XP machine.  It will install and run using wine but it doesn't download files.  It's just easy to launch my Virtualbox up every month and install the file to my MP3 player.

---

### Post by mndzmyst on 2007-12-08
I just found out how to download the .pl file. I have written a simple nautilus script to do so, but first you must install Audible manager with wine and activate it. Once downloaded I use Amarok to transfer to my ipod. :guitar:


 thanx goes to malik.net ([http://maulik.freeshell.net/Miki.pl?page=2007-03-22.miki](http://maulik.freeshell.net/Miki.pl?page=2007-03-22.miki)) for showing the way.

::EDIT::

I have also made it work with nautilus actions. Download the schema below and import it to nautilus-actions. You must have wine and audible manager installed

Installation:

(1) install wine
(2) install audible manager using wine and activate account
(3) import schemas using nautilus-actions

Path= wine '/home/YOUR_USERNAME_HERE/.wine/drive_c/Program Files/Audible/Bin/AudibleDownloadHelper.exe'

Parameter= %M

CONDITIONS:
Filenames: aw_dhelper.pl

Not much to it, but hey, I just started writing scripts

---

### Post by Deathmoon on 2007-12-25
I think that I have this figured out; it's not a direct method and requires a few nonfree items however.

1. VirtualBox
2.  WinXP virtual machine
3.  Nero 7 (or version 8)
4.  Audible Manager

VirtualBox will not allow you to [burn]("http://www.virtualbox.org/ticket/903") CD (or at least I have not been able to do so).  

Download your audiobook in XP using Audible Manager.  Once complete, open Nero and create an image (*.nrg) with your audiobook files.  Then, using the Nero ImageDrive; this creates a virtual cd/dvd rom.  Load the image you just created (*.nrg).

Now, open up your favorite audio ripper in Windows, and rip the CD (aka image).  From there, you can use the shared folder VirtualBox comes with to free up disk space on your XP VM.

---

### Post by Sami_Sdata on 2007-12-26
I'm running kubuntu with audible.  I installed audiblemanager with wine.  When downloading a book from audible I just choose "open with" and use ~/.wine/drive_c/Program Files/Audible/Bin/AudibleDownloadHelper.exe

When the download is complete I see the book in Audiblemanager.  I'm not home at the moment (working over vnc)  so I can't confirm that the file plays but since the manager recognizes it I don't see any problem.

---

### Post by sorba on 2008-06-11
I just installed Audible Manager in Wine.
I went to My Library Online and pressed download on a title. I Chose AudibleDownloadHelper.exe as the program to open with:
[http://www.thequiltfactory.com/Bilder/audible0.png]("http://www.thequiltfactory.com/Bilder/audible0.png")
It then opened a download box and started to download:
[http://www.thequiltfactory.com/Bilder/audible1.png]("http://www.thequiltfactory.com/Bilder/audible1.png")
It then popped up in the Library in Audible Manager:
[http://www.thequiltfactory.com/Bilder/audible2.png]("http://www.thequiltfactory.com/Bilder/audible2.png")
But I can't play it in the built in player, and it doesn't recognise my Sandisk Sansa m240. I have to open Amorok, connect the Sansa, and go to the Audible download folder and right click the audio file and transfer to device. It is then playable on the Sansa:)

---

### Post by dvystrcil on 2008-06-12
I am going to have to give this a try, but it won't be for awhile yet. I just re-built my machine and I need to 8.04 installed.

---

### Post by undecidable on 2008-06-29
I tried Audible Vsn 5 and the previous Vsn 4
using Wine 1 and Wine 1.1 (an update from the Ub repos today).

Audible 4 installs OK.
Audible 5 gives an error on installing, 
  (failed to register file C:\...\AudibleExt.dll)
but otherwise the install seems to work.

Both successfully import my audible files and seem to activate ok.

But when playing an audible file,
even the introductory "welcome to Audible" file,
they stop after 3 secs, and Audible hangs.

---

### Post by caish5 on 2008-06-30
I get a hang after 1 second. But this is so tantalizingly close there must be a simple fix. Unfortunately my linux skills are a little limited to come up with it myself.

---

