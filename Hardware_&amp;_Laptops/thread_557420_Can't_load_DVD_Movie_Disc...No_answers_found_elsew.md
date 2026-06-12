---
title: "Can't load DVD Movie Disc...No answers found elsewhere."
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by Jussayre on 2007-09-22
So, here goes.  I am not posting this question without doing considerably homework first.  I have searched throughout hundreds of posts on these forums, and tried everything I could find.  Anyone who can suggest things I might look at, I would be greatly appreciative.

Symptom:  I load a dvd movie into my combo CDRW/DVDRW drive on my Gateway 6520GZ Laptop.  The name of the DVD Movie appears on my desktop, and when I double click the icon, it shows me two files in an explorer window, Audio TS, and Video TS.  I am able to browse the contents of the disc with no delay.  

Then I open my copy of VLC Media Player (Because it appears to be the best supported), and select File, then Open Disc.

The following is what is displayed at the bottom of that screen by default:  dvd:///dev/scd0.  I then click OK, and can hear my computer spinning up the DVD Drive.  The large black window opens for the media player screen, a blue screen appears inside it like the start of the movie, and then almost instantaneously, the entire player shuts down.

The same thing happens with every media player I've tried.  Xine, GXine, MMPlayer, Ogle. I simply cannot get the laptop to properly run a dvd movie at all.  Once or twice, I heard the audio from the disc for about 2 seconds, before it shut down.

I did some homework, and the drive is an IDE drive, not SCSI.  I do have WINE installed, and i'm pretty sure WINE runs a SCSI emulator as part of the program.  Is this my problem?  How do I fix it?  What do I not know, what should I know?  Any help would be greatly appreciated.

---

### Post by kish on 2007-09-22
Same problem here.
Thought libdvdcss must solve it. Haven't given much thought.
Will try now.

---

### Post by Jussayre on 2007-09-22
I have reloaded the CSS files, the W32 files.  I have tried using Automatix2 to fill in any libraries I might be missing.  I have reinstalled my media players, updated my JAVA. Nothing has kept my player from closing when I play a DVD Movie.

I have tried also to install Virtualbox.  Virtualbox starts up fine, but when I try to install Windows XP as my virtual machine it continually gives me a FATAL error and won't load the CDrom.  I suspect this is another symptom of my same problem...

A quick note, the drive mounts and unmounts without a problem.

---

### Post by por100pre1 on 2007-09-22
For libdvdcss2 to add the [Medibuntu]("http://medibuntu.org") repository is an easy way. [Here's]("http://medibuntu.org/repository.php") how. Once the repository is added:

```
sudo apt-get update && sudo apt-get install libdvdcss2
```

---

### Post by lisati on 2007-09-22
Have a read of [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html), with the following in mind:
[LIST=1]
[*]Install the libraries with "sudo aptitude install xxxxx" from the terminal, without the quotes, and where "xxxxx" represents the library 
[*]Don't worry too much if the CSS library reports an error - sometimes the "setup" commands later in the post manage to pull it in....
[*]Don't worry too much about the setting of preferences to GXINE - use the player of your own choice
[*]Enjoy
[/LIST]

---

### Post by Jussayre on 2007-09-22
lisati, thanks for your input.  I have already tried the suggestions from the link you posted. To no avail.  And as for the libraries.  I have installed them all.  Nothing worked.

Any other suggestions?

As for the medibuntu repository....I have already tried that as well.  DIdn't change my outcome though.

---

### Post by Jussayre on 2007-09-22
Quick update.  I loaded an MPEG file off the net...and it too won't run in one of the media players.  However, streaming videos off the web run no problem.

---

### Post by bmannering on 2007-09-22
I was having a similiar problem where the dvd would almost load and then VLC would just quit. I figured it out that it doesnt work when compiz is on so i just alt F2 metacity --replace and it worked fine.
Hopefully this works but if it is more complicated i dont know.

---

### Post by Jussayre on 2007-09-22
bmannering - Thank you very much.

OK!!! So now my media player loads.  But all I get is Audio with a blue screen....

What do I need to do to get my video up on screen?  Again, I am using VLC Media Player.

---

### Post by Jussayre on 2007-09-22
OK SO I HAVE A SOLUTION

Check out the following link: [http://xinehq.de/index.php/faq](http://xinehq.de/index.php/faq)

You have to create a launcher command titled Play DVD with command line:  xine -V XShm

For whatever reason my XV kernal isn't loading with my Intel chipset.  This is the only way I could get my DVD to load.  If someone can tell me step by step how to make XV load, I'd be soo happy.

---

### Post by mschraier on 2007-11-05
I also had tried many players and so forth.  AFter installin libdvdcss2 and w32codecs, i installed Kaffeine thru Synaptic.  IT owkrs perfectly.  Give it a try

---

