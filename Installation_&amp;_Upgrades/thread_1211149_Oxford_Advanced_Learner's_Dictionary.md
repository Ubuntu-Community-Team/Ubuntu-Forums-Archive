---
title: "Oxford Advanced Learner's Dictionary"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by lordofallhearts on 2009-07-12
Hi all
I am posting this thread to help those who want to install Oxford Advanced Learner's Dictionary (7th edition software) in Ubuntu. In case you further need assistance , feel free

1.) Install libgtk1.2 from [http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)
     Install libcanberra-gtk-module from 
     [http://packages.ubuntu.com/jaunty/libcanberra-gtk-module](http://packages.ubuntu.com/jaunty/libcanberra-gtk-module)
     Even if libcanberra-gtk-module doesnt work , you can carry on with installation.
 
2.) Open your CD / Mounted image. In Linux folder double click Installation.sh
3.) Install the software with full installation. It installs in Home / Oald .
4.) Run the software by doubleclicking oald7 in the folder home / Oald. See if audio files are installed or not. If not , then reinsert CD / remount image and again go with installation. Install your audio files.

5.) Dictionary is installed but you'll find that fonts are too small.Hence you need to install the appropriate fonts.

Open a terminal window (Applications > Accessories > Terminal )

sudo apt-get install msttcorefonts 
[LEFT]cd /usr/share/fonts/truetype/msttcorefonts[/LEFT]

sudo cp Verdana * /usr/local/oald/fonts


After this open the folder Home / oald / fonts
and place the following content in fonts.dir



[COLOR="Blue"]9
DictBats.ttf-misc-DictBats-medium-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana.ttf-microsoft-Verdana-medium-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana_Bold.ttf-microsoft-Verdana-bold-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana_Italic.ttf-microsoft-Verdana-medium-i-normal - 0-0-0-0-p-0-iso8859-1
verdana.ttf-microsoft-Verdana-medium-r-normal - 0-0-0-0-p-0-iso8859-1
verdanab.ttf-microsoft-Verdana-bold-r-normal - 0-0-0-0-p-0-iso8859-1
verdanai.ttf-microsoft-Verdana-medium-i-normal - 0-0-0-0-p-0-iso8859-1

DictBats.ttf -altsys-DictBats-large-r-normal--0-0-0-0-p-0-ascii-0
DictBats.ttf -altsys-DictBats-large-r-normal--0-0-0-0-p-0-iso10646-1[/COLOR]

Now its done !!!!

---

### Post by munishvit on 2009-07-12
Thanks for the information..:p

---

### Post by oldos2er on 2009-07-12
You might want to post this to Tips & Tutorials.

---

### Post by helen_prag on 2009-08-05
I was used to Windows so, now I'm struggling with Linux. I hope I'll manage to install it.

---

### Post by lordofallhearts on 2009-08-06
In case you get stuck , or any other problem feel free to consult

---

### Post by ivanla on 2010-04-11
Hi,

I am running Karmic Koala 64bit and libgtk1.2 is no longer in the repository. I managed to add Jaunty repo to synaptic and it appeared so I could install it. But it seems that OALD7 requires 32bit version of it as the installer still does not start saying following:

> error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Couldn't load 'atal'
The setup program seems to have failed on x86/glibc-2.1

Please contact Loki Technical Support at [email]support@lokigames.com[/email]


 I would be grateful if anyone could advise on this matter.

---

### Post by viebuntu on 2010-04-11
Hi, 
I do have exactly the same problem as ivanla (failing installation of the OALD 7 Dictionary).
However without the mentioned "add[ing] Jaunty repo to synaptic"-part that ivanla mentions. I didn't try anything in this respect. I tried to install the packages mentioned in the first post by lordofallhearts from July 2009, however this fails due to wrong dependencies.


I'm running a 32-bit version: 
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Help will be greatly appreciated.
:confused:
Thanks.

---

### Post by meho_r on 2010-04-11
But, why not using StarDict, for which there are many dictionaries, one of them being The Oxford Advanced Learner's Dictionary?

---

### Post by ivanla on 2010-04-11
I have managed to start installer and install OALD7, however pronouncing still does not work.

I did following:
1. went to [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) for instructions on how to install getlibs as to install needed 32bit libraries on my 64bit OS.
2. Added dapper "deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe" repo to app sources.
3. Installed libgtk1.2 and others with the help of apt-get.
3. ran installation: linux32 ./installation.sh

@viebuntu
It seems to me you had better do the same as I did: add dapper repo to resolve dependencies.

---

### Post by ivanla on 2010-04-11
> **meho_r said:**
> But, why not using StarDict, for which there are many dictionaries, one of them being The Oxford Advanced Learner's Dictionary?
I would say that OALD7 has better functionality and the interface is much friendlier than one of StarDict.

---

### Post by elsdyr on 2010-04-15
Hi guys,
Ubuntu Karmic Koala user here. The sound in OALD doesn't play (it generally does on my system though). It's really been a struggle to use OALD on Ubuntu for me. The sound seems to work every second month and then *pow* all gone. I've been able to fix it until now, by the help of you gentlemen! So thank you. 

Now let's see what happens when I start the programme:

```
$ ./oald7 

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
[00000179] mp4 demuxer error: cannot find any /moov/trak
[00000179] id3 demuxer error: cannot peek()
[00000179] sap demuxer error: cannot peek
[00000179] real demuxer error: cannot peek
[00000179] pva demuxer error: cannot peek
[00000179] nsv demuxer error: cannot peek
[00000179] aiff demuxer error: cannot peek
[00000179] playlist demuxer error: cannot peek
[00000179] playlist demuxer error: cannot peek


```and then, every time I click on a speaker icon in an article to hear the pronunciation of a word, I get this:
```
[00000180] main input error: no suitable access module for `chrome://oald7/content/empty.mov'

```I have the following package
```

$ dpkg -s libcanberra-gtk-module | grep Status
Status: install ok installed

```
wat do?

---

### Post by huynhlv_54 on 2010-05-07
Hi. 
I have tried a lot to install OALD7 in ubuntu 10.04 <64 bit version>, but I can't. 
Please see the following code and help me if you can. I have downloaded and install libgtk1.2_1.2.10-18.1build2_amd64.deb. I'm very new to linux, so please guide step by step.
Great thank!

huynh@huynh-desktop:/media/cdrom/linux$ linux32 ./insta*.sh
Verifying archive integrity... All good.
Uncompressing OALD7..........................
/home/huynh/.setup30434: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Couldn't load 'atal'
The setup program seems to have failed on x86/glibc-2.1

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
The program returned an error code (1)

---

### Post by slimdee on 2010-05-17
Thank you, I've installed the dictionary in Ubuntu 10.04 following your instruction. Some dependent packages have to be install in advanced to the libgtk1.2. But finally, the program works perfectly.

---

### Post by susiriss on 2010-06-07
Actually you don't have to worry about enabling some repository of an older Ubuntu. There is nice hack you can do after installing ia32 libraries.


Go to "OALD8/linux/setup.data/bin/Linux" after you extract it to hard disk.
You'll find a dir named "**x86**". Just rename it to "**amd64**" and come back and run the setup.sh. 

Viola, the setup program runs. No need for gtklibs and old repos .!!!
Learned this from a thread which uses the trick for some other dictionary.
;-)

cheers !

---

### Post by Pacifik on 2010-06-25
Hi,
I have been trying to install OALD 7 in Ubuntu Lucid (10.04) after reading this thead. Double-click on the "installation.sh" file do not help to install it. Instead from the terminal I use to type:
$sudo sh ./installation.sh           (from the CD)

It gives no error. But "Oxford Advanced Language Setup" window, which pops up, looks blank with no writing/instruction on it. I couldn't understand what went wrong. I am attaching the screenshot for better understanding. Please suggest how to install it.

---

### Post by Pacifik on 2010-06-26
Please help me out ...

---

### Post by elsdyr on 2010-06-28
Pacifik try run it this way:

```
$sudo ./installation.sh
```otherwise I guess you miss some packages that OALD dependens on.

---

### Post by Pacifik on 2010-06-28
Thanks Elsdyr,
Since the "installation.sh" file is in CDROM, it cannot be executed (read-only). I have seen is a forum that $sudo sh ./installation.sh has worked for a ubuntu user.
[http://ubuntuforums.org/showthread.php?t=229965](http://ubuntuforums.org/showthread.php?t=229965)

I have copied the files/folders from the cdrom into hard disk. Executed it. Still same problem.

The font is not visible, in my case. Can it be some font issue?

---

### Post by vedi on 2010-07-02
> **lordofallhearts said:**
> Hi all
I am posting this thread to help those who want to install Oxford Advanced Learner's Dictionary (7th edition software) in Ubuntu. In case you further need assistance , feel free

1.) Install libgtk1.2 from [http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)
     Install libcanberra-gtk-module from 
     [http://packages.ubuntu.com/jaunty/libcanberra-gtk-module](http://packages.ubuntu.com/jaunty/libcanberra-gtk-module)
     Even if libcanberra-gtk-module doesnt work , you can carry on with installation.
 
2.) Open your CD / Mounted image. In Linux folder double click Installation.sh
3.) Install the software with full installation. It installs in Home / Oald .
4.) Run the software by doubleclicking oald7 in the folder home / Oald. See if audio files are installed or not. If not , then reinsert CD / remount image and again go with installation. Install your audio files.

5.) Dictionary is installed but you'll find that fonts are too small.Hence you need to install the appropriate fonts.

Open a terminal window (Applications > Accessories > Terminal )

sudo apt-get install msttcorefonts 
[LEFT]cd /usr/share/fonts/truetype/msttcorefonts[/LEFT]

sudo cp Verdana * /usr/local/oald/fonts


After this open the folder Home / oald / fonts
and place the following content in fonts.dir



[COLOR=Blue]9
DictBats.ttf-misc-DictBats-medium-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana.ttf-microsoft-Verdana-medium-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana_Bold.ttf-microsoft-Verdana-bold-r-normal - 0-0-0-0-p-0-iso8859-1
Verdana_Italic.ttf-microsoft-Verdana-medium-i-normal - 0-0-0-0-p-0-iso8859-1
verdana.ttf-microsoft-Verdana-medium-r-normal - 0-0-0-0-p-0-iso8859-1
verdanab.ttf-microsoft-Verdana-bold-r-normal - 0-0-0-0-p-0-iso8859-1
verdanai.ttf-microsoft-Verdana-medium-i-normal - 0-0-0-0-p-0-iso8859-1

DictBats.ttf -altsys-DictBats-large-r-normal--0-0-0-0-p-0-ascii-0
DictBats.ttf -altsys-DictBats-large-r-normal--0-0-0-0-p-0-iso10646-1[/COLOR]

Now its done !!!!
Thank you very much it helped me so much.

---

### Post by japcrword on 2010-08-24
> **ivanla said:**
> I have managed to start installer and install OALD7, however pronouncing still does not work.

I did following:
1. went to [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) for instructions on how to install getlibs as to install needed 32bit libraries on my 64bit OS.
2. Added dapper "deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe" repo to app sources.
3. Installed libgtk1.2 and others with the help of apt-get.
3. ran installation: linux32 ./installation.sh

Thanks for foolproof installation instructions. I've installed OALD7 on my 10.04 Lucid Lynx 64bit following them (apart for one thing: I used "deb [http://*cz.archive.ubuntu.com/ubuntu*]("http://%3Ci%3Ecz.archive.ubuntu.com/ubuntu%3C/i%3E") dapper main" instead of "... universe" as the latter didn't work out for me). It works precisely as you described. I mean, no sound. Have you managed to resolve the issue? (Or have anyone else on 10.04 amd64?) Actually it's a minor problem as there are good transcriptions. But still it's preventing my OALD7 from being "perfectly installed"...

Actually I'm a bit surprised of OALD's support of Linux. I've installed it on Win2K, Vista and Win7. And every installation it made a thorough (and error prone as it turned out) check that it runs from genuine CD. Now on Linux I copy it on my hard drive and run it no problem. It's very convenient. Why didn't they realize that with Windows?!

PS. I also have to say that I couldn't run installation directly from CD as it lacked 'eXecute' permission. I had to copy the files on my hard drive, run 'chmod a+x installation.sh' to invoke 'linux32 ./installation.sh'

---

### Post by ivanla on 2010-08-25
> **japcrword said:**
> It works precisely as you described. I mean, no sound. Have you managed to resolve the issue? (Or have anyone else on 10.04 amd64?) 

I have to say that I had just been inattentive to the issue with sound as I discovered later that it worked perfectly well. No assumptions why it didn't work for you, though. I hope you will find the solution because I've acceidentally broken my disc. I'm going to buy a new edition, 8th or possibly 9th (not sure which is the current one). Hope they've fixed the problems.

> **japcrword said:**
> 
Actually I'm a bit surprised of OALD's support of Linux. I've installed it on Win2K, Vista and Win7. And every installation it made a thorough (and error prone as it turned out) check that it runs from genuine CD. Now on Linux I copy it on my hard drive and run it no problem. It's very convenient. Why didn't they realize that with Windows?!
I'm afraid I have no idea of what you are saying. It never tried to check if it was running from genuine CD. It perfectly runs from the hard drive, though the CD is protected from copying.
> **japcrword said:**
> 
PS. I also have to say that I couldn't run installation directly from CD as it lacked 'eXecute' permission. I had to copy the files on my hard drive, run 'chmod a+x installation.sh' to invoke 'linux32 ./installation.sh'
I didn't experience such problem.

---

### Post by japcrword on 2010-08-25
> **ivanla said:**
> I have to say that I had just been inattentive to the issue with sound as I discovered later that it worked perfectly well.

Just as you said - the sounds works, confirmed. I found out what the problem was: It conflicts with other multimedia programs. For instance when I start VLC media player, play the music, then press pause, the sound in OALD7 doesn't work. But if I close VLC the OALD7's sound starts working. Same with other players: OALD7 is silent while you listening to the music (it prints "cannot open audio device (/dev/dsp)" on terminal).

> **ivanla said:**
> I'm afraid I have no idea of what you are saying. It never tried to check if it was running from genuine CD. It perfectly runs from the hard drive, though the CD is protected from copying.

I meant the installer, not the installed program. It's secuROM protected, hence the installer won't run from hard drive (nor from ordinary CD image).

---

### Post by ivanla on 2010-08-26
> **japcrword said:**
> It conflicts with other multimedia programs. 
A pesky issue, isn't it? :) 

> **japcrword said:**
>  I meant the installer, not the installed program. It's secuROM protected, hence the installer won't run from hard drive (nor from ordinary CD image).
All right. But I did manage to start the installer from the CD. The installer had proper permission in my case.

---

### Post by gpdas on 2010-09-01
I am using Ubuntu 10.04
While downloaded and installed libgtk1.2 the following error came.

Package : libgtk1.2
Status:  Error: Dependancy is not satifiable
            libglib1.2ldbl(>= 1.2.10-18)

The GIMP Toolkit set of widgets for X
The GIMP Toolkit is a freely available set of widgets for X. GTK is easy to use, and has been implemented in such projects as The GNU Image Manipulation Program (The GIMP), GNOME, a GNU desktop set of utilities for X, and gzilla, a GNU web-browser. 

I am not able to install OALD7.

---

### Post by moe.k on 2010-09-11
Hello,

please note if you use a 64 bit system and get this error message:

```
The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
```

Use the following command to execute setup.sh:

```
linux32 ./setup.sh
```

Thanks to [http://ubuntuforums.org/showpost.php?p=8705232&postcount=1#1](http://ubuntuforums.org/showpost.php?p=8705232&postcount=1#1)

I am using Ubuntu 10.04 and 8th edition of Oxford Advanced Learner's Dictionary.

Regards,
moe.k

---

### Post by Pacifik on 2010-09-30
> **Pacifik said:**
> Hi,
I have been trying to install OALD 7 in Ubuntu Lucid (10.04) after reading this thead. Double-click on the "installation.sh" file do not help to install it. Instead from the terminal I use to type:
$sudo sh ./installation.sh           (from the CD)

It gives no error. But "Oxford Advanced Language Setup" window, which pops up, looks blank with no writing/instruction on it. I couldn't understand what went wrong. I am attaching the screenshot for better understanding. Please suggest how to install it.

Hi friends,
I am evoking this thread again. After couldn't able to install OALD7 in ubuntu 10.04 32 bit system, I buyed a OALD8 CD to try my hands out. But the issue remains the same. The fonts are not visible. When tried to run the "setup.sh" file through terminal the following error/warning could be seen (pl see the screen shot). But "libcanberra-gtk-module" is installed.

[I]ujjal@ubuntu:~/Documents/OALD8/linux$ dpkg -l | grep libcanberra-gtk-module
ii  libcanberra-gtk-module                    0.22-1ubuntu2                                   translates Gtk+ widgets signals to event sou
ii  libcanberra-gtk-module-dbg                0.22-1ubuntu2                                   libcanberra GtkModule detached debugging sym

[/I]
I am attaching the screenshot for better understanding. The screenshot says the fonts are not visible and some problem with libcanberra-gtk-module. Could you expert guys sort out my problems, since this is acting as a ulcer to me now.

---

### Post by Pacifik on 2010-10-01
> **Pacifik said:**
> Hi friends,
I am evoking this thread again. After couldn't able to install OALD7 in ubuntu 10.04 32 bit system, I buyed a OALD8 CD to try my hands out. But the issue remains the same. The fonts are not visible. When tried to run the "setup.sh" file through terminal the following error/warning could be seen (pl see the screen shot). But "libcanberra-gtk-module" is installed.

[I]ujjal@ubuntu:~/Documents/OALD8/linux$ dpkg -l | grep libcanberra-gtk-module
ii  libcanberra-gtk-module                    0.22-1ubuntu2                                   translates Gtk+ widgets signals to event sou
ii  libcanberra-gtk-module-dbg                0.22-1ubuntu2                                   libcanberra GtkModule detached debugging sym

[/I]
I am attaching the screenshot for better understanding. The screenshot says the fonts are not visible and some problem with libcanberra-gtk-module. Could you expert guys sort out my problems, since this is acting as a ulcer to me now.

Hi friends,
I have sorted out the issue. Well it would be right to say that I was able to install the OALD8 (oxford advanced learner's dictionary, 8th edition).

The font was still invisible. But I manage to search in google that without seeing any font, oald8 can still be able to install it in ubuntu 10.04 (32 bit). Let me enumerate the installation procedure:

1. Copy the CD in hard disk.
2. browse into to the directory "linux"
3. You will find a file "setup.sh". Make it executable.
4. 'Run' the file by double clicking on it.
5. I haven't been able to see the font (pl see the screen shot). Still clicked the right-hand option (screen shot 1).
6. Then again clicked the right-hand option (screen shot 2).
7. The installation will start. Within few seconds the installation will complete. (I was not able to see the font again, while installation) Hopefully an icon will be created on the desktop, when the installation is complete. Make it executable via command line ($chmod +x oald8.desktop)
8. You can find the icon changes to OALD8 icon. Now you can launch the OALD8 application by double clicking it.

Before the OALD8 installation, I have installed "libgtk1.2 1.2.10-18.1build2" and "libcanberra-gtk-module 0.22-1ubuntu2".

I hope I was comprehensive enough to discuss the steps of installation. This thread may be helpful to the tyros.

Enjoy using Ubuntu!

Regards
Pacifik

---

### Post by Viva on 2010-12-02
Just installed it on maverick. The resources are not working for some reason. I click on one of them and nothing happens.

---

### Post by den2042 on 2010-12-11
Fore me oald8 works perfectly with sound on amd64 ubuntu system after 

linux32 ./setup.sh  So thank you very much.

To enable sound in oald8 on i386 systems you may try to find packages
festival
festlex-oald
Those are packages in debian. It worked well on debian. Hopefully it might work on ubuntu also.

---

### Post by Viva on 2010-12-11
> **den2042 said:**
> Fore me oald8 works perfectly with sound on amd64 ubuntu system after 

linux32 ./setup.sh  So thank you very much.

To enable sound in oald8 on i386 systems you may try to find packages
festival
festlex-oald
Those are packages in debian. It worked well on debian. Hopefully it might work on ubuntu also.

Do the resources work for you?

---

### Post by electrosicodelic on 2011-01-05
In my experience oald8 works, I have to install festival package to enable sound but only "resources" doesn't work.
Someone knows how to fix it

---

### Post by Repgahroll on 2011-01-19
Hello guys... I've managed to install the dictionary (v8) on my Ubuntu setup (32bit), but for some reason, it asks for the CD-ROM (Please insert the Oxford A.L.D. CD-ROM), If I click "cancel" it's possible to use the dictionary partially... because when i try to double-click a word, it asks for the CD again.

Maybe it's a bug, because if the content is installed on HD, why would it ask for the CD?

Please, somebody help me because I really need to use this dictionary.

Thank you.

---

### Post by Repgahroll on 2011-01-19
Hello guys... I've managed to install the dictionary (v8) on my Ubuntu setup (32bit), but for some reason, it asks for the CD-ROM (Please insert the Oxford A.L.D. CD-ROM), If I click "cancel" it's possible to use the dictionary partially... because when i try to double-click a word, it asks for the CD again.

Maybe it's a bug, because if the content is installed on HD, why would it ask for the CD?

Please, somebody help me because I really need to use this dictionary.

Thank you.

---

### Post by Repgahroll on 2011-01-19
Hello guys... I've managed to install the dictionary (v8) on my Ubuntu setup (32bit), but for some reason, it asks for the CD-ROM (Please insert the Oxford A.L.D. CD-ROM), If I click "cancel" it's possible to use the dictionary partially... because when i try to double-click a word, it asks for the CD again.

Maybe it's a bug, because if the content is installed on HD, why would it ask for the CD?

Please, somebody help me because I really need to use this dictionary.

Thank you.

---

### Post by huynhdatcaptain on 2011-01-22
> **den2042 said:**
> Fore me oald8 works perfectly with sound on amd64 ubuntu system after 

linux32 ./setup.sh  So thank you very much.

To enable sound in oald8 on i386 systems you may try to find packages
festival
festlex-oald
Those are packages in debian. It worked well on debian. Hopefully it might work on ubuntu also.

i'm using ubuntu 10.1 and it definitely work for me! thanks alot

---

### Post by ubuscout on 2011-04-01
Unluckly I've an older version of longman dictionary, exactly  4v2... btw, following many hints available here and somewhere, I managed quite fine installing it but sound doesn't work at all

here the output:
[00000179] mp4 demuxer error: cannot find any /moov/trak
[00000179] id3 demuxer error: cannot peek()
[00000179] sap demuxer error: cannot peek
[00000179] real demuxer error: cannot peek
[00000179] pva demuxer error: cannot peek
[00000179] nsv demuxer error: cannot peek
[00000179] aiff demuxer error: cannot peek
[00000179] playlist demuxer error: cannot peek
[00000179] playlist demuxer error: cannot peek

...and if I click any speaker icon, this follow:
[00000180] main input error: no suitable access module for `chrome://ldoce/content/empty.mov'
[00000188] mpeg_audio packetizer: MPGA channels:1 samplerate:16000 bitrate:24
[00000189] mpeg_audio decoder: MPGA channels:1 samplerate:16000 bitrate:24
[00000190] oss audio output error: cannot open audio device (/dev/dsp)
[00000190] main audio output error: couldn't find a filter for the conversion
[00000190] main audio output error: couldn't set an output pipeline


I tried installing as normal user, then by sudo... but I face always the same problem...

..any hint ? plz I find really useful sound feature and I need it...

thx in advance

ps. mine is ubuntu 10.10 x86
uname -a ---> Linux pulsarx 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

---

### Post by jacarandansw on 2011-04-01
oh yeah!

---

### Post by Guillu on 2011-04-11
Hi people!

I'm having trouble installing OALD7 in Maverick. I installed Ubuntu in Spanish so I'll try to do my best to translate the error message:

_Spanish_:
**No se puede abrir el archivo /media/OALD7/linux/installation.sh.**
gedit no pudo detectar la codificación de caracteres.
Compruebe que no está intentando abrir un archivo binario.
Seleccione una codificación de caracteres desde el menú e inténtelo de nuevo.
Codificación de caractéres: Occidental (ISO-8859-1)

_English_:
**[I]File /media/OALD7/linux/installation.sh can't be opened.**
gedit couldn't detect the character encoding.
Check that you are not trying to open a binary file.
Choose a character encoding from the menu and try again.
Character encoding: Occidental (ISO-8859-1)[/I]

I tried with every and each character encoding (yeah, I'm actually that new in ubuntu) but nothing happened.
I would really appretiate a litlle help here, since I work with that dictionary every day... Thank you!

---

### Post by heroandtn3 on 2012-08-04
> **den2042 said:**
> Fore me oald8 works perfectly with sound on amd64 ubuntu system after 

linux32 ./setup.sh  So thank you very much.

To enable sound in oald8 on i386 systems you may try to find packages
festival
festlex-oald
Those are packages in debian. It worked well on debian. Hopefully it might work on ubuntu also.

Don't work for me :(

Can I help me enable sound in oald8? I'm using Ubuntu 12.04.

---

### Post by ubudog on 2012-08-04
> **heroandtn3 said:**
> Don't work for me :(

Can I help me enable sound in oald8? I'm using Ubuntu 12.04.

Hi heroandtn3 -- this is an old thread and it would be better to start a new thread.

Thread closed.

---

