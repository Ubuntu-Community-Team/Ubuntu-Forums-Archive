---
title: "What's the best dvd rip program?"
date: 2008-11-08
forum: General Help
---

### Post by kokkus on 2008-11-08
HI.
I am looking for a program to rip dvd's with.
I've tried 100s of free programs that doesn't even work.
Please tell me a good dvd ripping program.
Thanks:)

---

### Post by Steve1961 on 2008-11-08
k9copy is very good for backing up a commercial dvd to an iso file, and dvdrip is good for ripping into an avi file

---

### Post by SuperSonic4 on 2008-11-08
k9copy can also rip to avi, I've just done a test file and it's playing in xine as I speak

---

### Post by Steve1961 on 2008-11-08
> **SuperSonic4 said:**
> k9copy can also rip to avi, I've just done a test file and it's playing in xine as I speak

You're right, I forgot it could do that too :D

---

### Post by kokkus on 2008-11-08
Great thanks!
I'll try that program.

---

### Post by SuperSonic4 on 2008-11-08
> **Steve1961 said:**
> You're right, I forgot it could do that too :D

It doesn't play in VLC or Dragonplayer though but smplayer is a success

---

### Post by Locutus_of_Borg on 2008-11-08
acidrip works very well for me

---

### Post by kokkus on 2008-11-08
How do I know it's working? When I start the prosess nothing happens (i suppose).
Does any other programs out there work to rip to avi format?

---

### Post by Locutus_of_Borg on 2008-11-08
acidrip defaults to .avi but you can change it various other formats

to observe the progress, once it starts, click on the full view button, then the debug button


or if you are 1337 (lol) just use mencoder

---

### Post by kokkus on 2008-11-08
I tried acidrip but when I start the program, loads the dvd directory nothing happens, it finds the dvd under /media but the program freezes and does nothing.

---

### Post by kevdog on 2008-11-08
Too bad ImgBurn doesn't have a Linux Version

---

### Post by Chunky Dunk on 2008-11-09
There's also DVDShrink... Its a Windows program, but it works great with wine

---

### Post by SuperSonic4 on 2008-11-09
> **kokkus said:**
> How do I know it's working? When I start the prosess nothing happens (i suppose).
Does any other programs out there work to rip to avi format?

With k9copy you have to open the dvd so it appears and then you have to check the box you want to rip. Pressing mpeg4 or mpeg2 will come up,pick a directory to save to and you'll see it going on the right panel

---

### Post by lakerssuperman on 2008-11-09
I would have to say that Handbrake is far and away the best ripper in terms of speed and ease of use.  As far as I know this is the only ripper that fully utilizes all cores of your CPU.  I can do a 2-pass rip of a dvd inside of 40 minutes.  Also, I find that the presets are good for most things and tweaking of settings is relatively easy.  You won't find the enormous amount of features that something like dvd:rip has but, it has a good amount to play with.

Here is a link where you can find the debs of a recent build.  I am running it now and it is stable and fast.  Stay classy.

[http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html](http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html)

---

### Post by kokkus on 2008-11-09
Hmm. This is odd. None of these programs mantioned here seems too work or won't rip my dvd. Maybe it's protected in some wway?
Is there any other programs I can use to rip the dvd or convert vob to avi?
Thanks in advance:)

---

### Post by Steve1961 on 2008-11-09
make sure you have installed libdvdcss2 to deal with any encryption

---

### Post by kokkus on 2008-11-09
Thanks. I will give Handbrake a chance if only someone could give me a deb link that works. Please not rapidshare links. 
Thanks.
And thank you guys for all your help with this.

---

### Post by m_duck on 2008-11-09
For libdvdcss2, the easiest way is enabling the [medibuntu repo]("https://help.ubuntu.com/community/Medibuntu") and then installing the package:```
sudo apt-get install libdvdcss2
```

I like dvd::rip for ripping dvds though I haven't used it in a while, and there a LOADS of options to play with so it takes a while to get used to.

Also, I just accidentally found [this page about dvd ripping]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs").

---

### Post by pete on 2008-11-09
Ditto on dvd::rip...  far and away the best DVD ripping software

---

### Post by kokkus on 2008-11-09
thanks but it didnt find the libdvdcss2 package.

---

### Post by oldos2er on 2008-11-09
After you enable the Medibuntu repository, you need to run "sudo apt-get update" in a terminal.

---

### Post by anjilslaire on 2008-11-09
> **Steve1961 said:**
> make sure you have installed libdvdcss2 to deal with any encryption

Bear in mind, libdvdcss2 doesn't get around newer copy protections such as [ARccOS]("http://en.wikipedia.org/wiki/ARccOS_Protection"), which just make a mess of the DVD standard.

Currently, there are no native Linux apps that can defeat some of these newer schemes. To get around it, you can run DVDFab HD Decrypter (free version) under wine to get the files to your hard drive, then use K9Copy or DVDShrink to get it down single layer size.
I have a tutorial [here]("http://anjilslaire.wordpress.com/2008/08/21/dvd-ripping-linux-style/").

---

### Post by stinger30au on 2008-11-09
install wine
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and then run dvdfab free
[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

---

### Post by brento73 on 2008-11-13
Does anyone know of an easy way to make an ISO of a data dvd? Everything mentioned/linked here has been centered on region codes and video formats, but I just want to be able to make backups of software DVDs, etc.

---

### Post by rbmorse on 2008-11-13
Brento, try this from a terminal:

dd if=/dev/cdrom of=/*pathandfilename*.iso

---

### Post by spibou on 2008-11-14
> **anjilslaire said:**
> Bear in mind, libdvdcss2 doesn't get around newer copy protections such as [ARccOS]("http://en.wikipedia.org/wiki/ARccOS_Protection"), which just make a mess of the DVD standard.

Currently, there are no native Linux apps that can defeat some of these newer schemes.
Are you sure about that? The Wikipedia link you gave says:
> 
RipIt for the Mac, Slysoft's AnyDVD, Fengtao's DVDFab Decrypter, RipIt4Me + DVD Decrypter, FixVTS, DVD43, MacTheRipper, along with VLC media player[1], GNU ddrescue, dd_rescue and MPlayer/MEncoder (for Linux) are usually able to overcome ARccOS.

---

### Post by andrew.46 on 2008-11-14
Hi,

I suspect that you might actually mean rip *and* convert? For purely ripping you could always try vobcopy. To rip an entire dvd simply:

```
$ vobcopy -m 
```

From the man page:

>   -m, --mirror
     mirrors  the  whole  dvd to harddisk. It will create a directory
     named after the dvd and copy the ifo, bup and vob  files  there.
     The title-vobs are decrypted during this.


  Andrew

---

### Post by charlieab1 on 2008-11-23
I have found the same problem with acidrip it can't seem to load the dvd files. any help will be great

---

### Post by brunoscunha on 2008-11-23
> **Chunky Dunk said:**
> There's also DVDShrink... Its a Windows program, but it works great with wine

You're lucky, for runing dvdshrink under wine, it doesn't even shows the dvd drives. And when I selected one it says not ready.
AARRRGGHHHH !!!!!!!!!

---

### Post by anjilslaire on 2008-11-23
After inserting the DVD, open it in your file browser, nautilus/dolphin/thunar/etc first, then close it, and open DVDShrink 2nd. It always seems to need to be mounted in browser first for me, then Shrink will see it.

Also, make sure Wine is configured correctly for your optical drives.

---

### Post by AAOFan on 2008-11-23
dvd:rip is about the most option intense program out there. I would only recommend this program for someone experienced in dvd ripping. It can rip dvds fast to avi if you don't mind a large file size (4.7-9GB). So my recommendation would be:

Experienced user:
dvd::rip

Novice:
K9 copy

Linux newbie:
wine-DVDshrink


My 2¢ and my first post!:guitar:

---

### Post by Biciclettapc on 2008-11-23
DvdShrink for ripping

and

Handbrake for decoding to other formats.  Handbrake has some preset buttons that do the basic settings.

Sort of going through that right now and so far those 2 are the best.  I am having to run them under win-blows but moving back to Ubu to edit (I hope)

I've used dvdshrink for several years and its always worked very well.  If you have Nero installed will burn copy straight to disk after its ripped

---

### Post by phidia on 2008-11-24
sorry double posted-but i only clicked once. :(

---

### Post by phidia on 2008-11-24
I might have a look at handbrake acidrip has the worst user interface I could imagine.
When you click start the app closes as if it crashes-the only indication something is happening is the flashing light on the optical drive.

---

### Post by mushy_t on 2008-12-03
I have a whole bunch of DVDs that I want to rip to avi or mpeg for editing. The first couple of discs worked fine, using Blaze Media Pro, but the rest of them - I've tested 8 of the remaining discs - simply won't rip. 
The DVDs will play on my computer (which is windows vista), but Blaze freezes when it tries to read DVD contents for ripping. I have since tried DVDx and Auto Gordion Knot with similar results... I have also tried it on a friend's computer using Blaze and it just ripped about 5% of the contents. 
The DVDs are not copy-protected in any way; they are home movies only, converted from VHS originally. Please please help me!!

---

### Post by sosaudio1 on 2008-12-03
> **mushy_t said:**
> I have a whole bunch of DVDs that I want to rip to avi or mpeg for editing. The first couple of discs worked fine, using Blaze Media Pro, but the rest of them - I've tested 8 of the remaining discs - simply won't rip. 
The DVDs will play on my computer (which is windows vista), but Blaze freezes when it tries to read DVD contents for ripping. I have since tried DVDx and Auto Gordion Knot with similar results... I have also tried it on a friend's computer using Blaze and it just ripped about 5% of the contents. 
The DVDs are not copy-protected in any way; they are home movies only, converted from VHS originally. Please please help me!!


OK how were these home movies made? Did you import them into a system? Or did you use a standalone DVD recorder? If you used a recorder, did you use the recorder to finalize the discs? What media did you use? Are you using +/- R or RW? 

If you didnt finalize it, you can use a program called ISO Buster thru Wine to break it out of the disc. 

Are these VCD discs? IE this is a CD that has video on it. This may require different software to remove the video from the disc.

Hope this gets you started

---

### Post by anjilslaire on 2008-12-03
> **phidia said:**
> I might have a look at handbrake acidrip has the worst user interface I could imagine.
When you click start the app closes as if it crashes-the only indication something is happening is the flashing light on the optical drive.

Strange. It works great here. For me it compresses to a small window mid-screen, with the option to show full size. And, the small window has details like time elapsed, etc.

---

### Post by mushy_t on 2008-12-03
> **sosaudio1 said:**
> OK how were these home movies made? Did you import them into a system? Or did you use a standalone DVD recorder? If you used a recorder, did you use the recorder to finalize the discs? What media did you use? Are you using +/- R or RW? 

If you didnt finalize it, you can use a program called ISO Buster thru Wine to break it out of the disc. 

Are these VCD discs? IE this is a CD that has video on it. This may require different software to remove the video from the disc.

Hope this gets you started

I used an LG VHS-DVD recorder, and I finalised all the discs which are DVD+R. I did all of them the exact same way, so I'm confused as to why the first couple worked and now the rest just make the ripping programs crash.

---

### Post by prince_niceguy on 2008-12-03
> **lakerssuperman said:**
> I would have to say that Handbrake is far and away the best ripper in terms of speed and ease of use.  As far as I know this is the only ripper that fully utilizes all cores of your CPU.  I can do a 2-pass rip of a dvd inside of 40 minutes.  Also, I find that the presets are good for most things and tweaking of settings is relatively easy.  You won't find the enormous amount of features that something like dvd:rip has but, it has a good amount to play with.

Here is a link where you can find the debs of a recent build.  I am running it now and it is stable and fast.  Stay classy.

[http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html](http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html)


I second that... It is amazingly fast compared to dvdrip. Dvd rip took 15 minutes to grab the preview, handbrake it was as soon as i loaded the dvd it got the preview and using preset of film, i was all set. ofcourse you can tweak yourself for further need... all in all handbrake rocks.

---

### Post by anjilslaire on 2008-12-04
It appears that jdong is creating a PPA to host handbrake debs, so we can all install it easily from a repo:
[https://launchpad.net/~handbrake-ubuntu]("https://launchpad.net/~handbrake-ubuntu")

---

### Post by prince_niceguy on 2008-12-04
> **anjilslaire said:**
> It appears that jdong is creating a PPA to host handbrake debs, so we can all install it easily from a repo:
[https://launchpad.net/~handbrake-ubuntu]("https://launchpad.net/~handbrake-ubuntu")

thats great... I downloaded it from their site for a 64 bit processor .... they have both... maintaining repository is a good idea.

---

### Post by anjilslaire on 2008-12-04
grrr.
How do I add a whole video_ts folder in the source?

---

### Post by prince_niceguy on 2008-12-04
> **anjilslaire said:**
> grrr.
How do I add a whole video_ts folder in the source?

Just add the parent folder of the VIDEO_TS as the source and it will detect it. I am referring to the handbrake. DVDRIP also same way...

---

### Post by anjilslaire on 2008-12-04
ah, yup. Found it in the GUI, there's a check box in the Select Source window, Open VIDEO_TS Folder. That does it :)

Thanks folks!

---

### Post by genothomas on 2010-04-28
> **kokkus said:**
> HI.
I am looking for a program to rip dvd's with.
I've tried 100s of free programs that doesn't even work.
Please tell me a good dvd ripping program.
Thanks:)
I tried almost all.
Best I found is Handbrake (in terms of clarity but low speed conversion than others)

---

### Post by tobemem on 2010-04-28
May I suggest ANDREW? My opinion could be biased, since I wrote it by myself, but I think you could find it useful. It's easy to install and all its dependencies are in Ubuntu repositories:

[http://tobemem.memebot.com]("http://tobemem.memebot.com/")

---

### Post by salala123456 on 2010-07-20
i use the the **iOrgSoft DVD to iPod Converter** .and it works well!,if you need any help please email me 
[EMAIL="salala1212@gmail.com"]salala1212@gmail.com[/EMAIL]. i will try my best ~ or you can goole "site:softwarebbs **iOrgSoft DVD to iPod Converter "**
 
or   [http://www.google.com.hk/search?hl=en&source=hp&q=site+%3Asoftwarebbs++iOrgSoft+DVD+to+iPod+Converter&btnG=Google+Search&rlz=1R2GGLL_zh-CNCN386&aq=f&aqi=&aql=&oq=&gs_rfai]("http://www.google.com.hk/search?hl=en&source=hp&q=site+%3Asoftwarebbs++iOrgSoft+DVD+to+iPod+Converter&btnG=Google+Search&rlz=1R2GGLL_zh-CNCN386&aq=f&aqi=&aql=&oq=&gs_rfai")=

[LIST]
[*][FONT=&#23435]Convert DVD to iPod audio [/FONT][FONT=&#23435]Select DVD subtitle and audio track [/FONT]
[*][FONT=&#23435]Advanced Video Encoding Settings [/FONT]
[*][FONT=&#23435]Merge into One file[/FONT]
[*][FONT=&#23435]Trim any DVD title chapter[/FONT]
[*][FONT=&#23435]DVD Video Cropping[/FONT]
[*][FONT=&#23435]Adjust DVD Video Effect[/FONT]
[*][FONT=&#23435]Video Snapshot[/FONT]
[/LIST]

---

