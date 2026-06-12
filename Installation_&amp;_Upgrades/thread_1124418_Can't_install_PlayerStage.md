---
title: "Can't install Player/Stage"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by carlosgoac on 2009-04-13
Hi!

I'm kinda new here with Ubuntu and I need to install Player/Stage for robot manipulation. I already installed Player but Stage just doesn't let to be installed, I already tried several ways: First by downloading the packages and installing them but it doesn't seem to work, I get some errors when entering the "make" command. The instructions in the INSTALL file just say ./configure then make and finally make install which is really easy but it doesn't work and there are no explanation on the errors and in the DEPENDENCIES file I downloaded and installed everything that is needed but when getting to the glib installation I get more errors. Then I tried using the apt-get install way and it worked just fine, it downloaded and installed a lot of stuff but at the terminal when hitting the command "player" it shows the instructions on how to run things but when putting "stage" tells me command not recognized. Finally I tried with the Synaptic Package Manager and it also tells me Stage is already installed so I decided to reinstall it with the Synaptic Manager but it doesn't work. Can anyone help me? I'm kinda fed up with this stuff, someone told me to check on the environment variables so I can check if it's really installed or perhaps something to do with the path or whatever. I'm desperate!

Regards!

---

### Post by jgurzoni on 2009-04-16
Carlos, hello
I'm also not an expert, but have you tried this link below ? look at the dependency files table on the right corner and make sure you have them all installed. you may want to try using synaptic to checkup/install
[http://www.control.aau.dk/~tb/wiki/index.php/Installing_Player_and_Stage_in_Ubuntu](http://www.control.aau.dk/~tb/wiki/index.php/Installing_Player_and_Stage_in_Ubuntu)

I'd also recommend you remove any player/stage version you already have before to try to install and use make clean before to try a new make.

---

### Post by carlosgoac on 2009-04-20
Hi J!

Thanks a lot for the link it was extremely helpful, I still had some other problems which were solved quickly by editing the .bashrc file and creating a rgb.txt file, now I believe it's finally installed. Hope we can collaborate further!

---

### Post by carlosgoac on 2009-04-21
I got some other problems though, when executing the simple.cgf located in the stage folder (i.e. player /usr/local/share/stage/worlds/simple.cfg) is supposed to open a new window with the map but it just doesn't and I don't know why. The last lines I get after executing the CFG file are:

 Stage driver creating 1 device
   6665.31.0 is a Stage world [Loading /usr/local/share/stage/worlds/simple.world][Include pioneer.inc][Include map.inc][Include sick.inc]


After that it just stays idle.

Can someone help me with this?

---

### Post by jgurzoni on 2009-05-03
Hello there again. 
I ran into the same issue you had when using Ubuntu 8.10 (intrepid), but I thought it was related to the fact that I run Ubuntu as a VMWare machine. I got tired later, removed everything and installed the player/stage packages that are available via apt-get/synaptic. it's a little bit older version, 2.0.3 for stage and 2.0.4 for player, but it worked just fine. the package names are robot-player and stage

after installing all I had to do was to create the rgb.txt file in /usr/X11R6/lib/X11/ as the article I gave you describes.

** in this install to run Player you type 'robot-player' instead of 'player'

cheers

---

### Post by carlosgoac on 2009-05-25
Good to know!

I will try that and tell you what happened, maybe we should have a better contact through skype or google talk or whatever, let me know what you think so we can colaborate together in these matters.

By the way, I took another aproach before using the synaptic, trying to use SVN, didn't work, I just got a Segmentation Fault when attempting to open a .cfg file.

Cheers!

---

### Post by gauravsc on 2009-09-19
Hi everyone i hav been trying to install player stage for some time and player got installed just fine but the stage is giving the error 

gaurav@gaurav-desktop:~/playerstage/Stage$ make
Linking CXX shared library libstage.so
/usr/bin/ld: cannot find -lLTDL_LIB
collect2: ld returned 1 exit status
make[2]: *** [libstage/libstage.so.3.2.0] Error 1
make[1]: *** [libstage/CMakeFiles/stage.dir/all] Error 2
make: *** [all] Error 2
i tried to install it from synaptic and it did the instalation but later when i ran the command player simple.cfg it shud hav opened a map whereas it said

error   : error loading plugin: stageplugin
error   : failed to load plugin: stageplugin
error   : failed to parse config file simple.cfg

can anyone help me i know you people r really good and thanx in advance....

---

### Post by irisorn on 2010-02-03
Hi,
I'm recently install Player/Stage on my ubuntu 9.04. This link help me with some installation problems. I hope this helps you too.

[http://www.thelastthule.com/index.php?option=com_content&view=article&id=13:gonho&catid=6:ubuntu&Itemid=2](http://www.thelastthule.com/index.php?option=com_content&view=article&id=13:gonho&catid=6:ubuntu&Itemid=2)

regards ;)

---

### Post by Arkapravo on 2010-03-16
Use **sudo apt-get install robot-player **

However, most of the player commands have to be modified to robot-player.

---

### Post by leo.adolpho on 2010-03-19
> **jgurzoni said:**
> Hello there again. 
I ran into the same issue you had when using Ubuntu 8.10 (intrepid), but I thought it was related to the fact that I run Ubuntu as a VMWare machine. I got tired later, removed everything and installed the player/stage packages that are available via apt-get/synaptic. it's a little bit older version, 2.0.3 for stage and 2.0.4 for player, but it worked just fine. the package names are robot-player and stage

after installing all I had to do was to create the rgb.txt file in /usr/X11R6/lib/X11/ as the article I gave you describes.

** in this install to run Player you type 'robot-player' instead of 'player'

cheers
Dear jgurzoni,
I've been facing the same problems described by carlosgoac and I'm following your tips. At your message, you mentioned about an article that teach us how to create the  rgb.txt file in /usr/X11R6/lib/X11. Could you, or carlosgoac, please send me that article ? Thanks a lot and I apreciatted your help !

---

### Post by Arkapravo on 2010-03-21
Yep ! ...... **apt-get install robot-player** works great @ Ubuntu 9.10 ..... however many interesting features do not work  ! ..... I guess they are only there in player/ stage 3.XX versions ! ...

---

### Post by haroldsoh on 2010-07-13
Hi, 

I managed to get PlayerStage (the latest development version) and Stage 3.0.2 working under Ubuntu 10.4. I wrote a simple script to take care of the dependencies and install gearbox, along with PlayerStage (which you can easily modify for your needs). You can download it at:

[http://www.haroldsoh.com/tutorials/technical-skills/installing-playerstage-from-2/](http://www.haroldsoh.com/tutorials/technical-skills/installing-playerstage-from-2/)

Hope this helps! I've only tested it on 10.4 so, let me know if you're experiencing problems and perhaps I can help. 

Harold

---

