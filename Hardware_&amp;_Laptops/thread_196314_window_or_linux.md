---
title: "window or linux???"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by alexohara1 on 2006-06-14
hi to all :) 
im only new to linux and ubuntu.... :rolleyes: 
and am tring to make the switch over from windows.... [-X 
Why? you ask...well,... i have found that there is alot of open source software whih i need...i have all this software on windows, which i bought long before i knew a thing...anyways...i have ubuntu 5.04 and there are a few question id liked answer if somene out there really knows...
(1) can i link up my laptop (ubuntu box) with my pc (XP box) via network cards and cable
(2) hook up to the net on my laptop
(3) id like to install neatbeans5.1 it is a linux download from java and ends in .bin (id imagine binary format) so how to do this from the terminal window
(4)At this site [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) 
below the heading of Drivers For Lucent Modems or similar...it says this....[To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:] 
so how do i create a file is it mkdir /etc/udev/rules.d or is it done seperatly

Finally, please if you have the answers...make sure there simple step by step guides...im still a dummy to this system but id like to give it a go....
i have been to linmodem.org and have download the modem tool,,, installed it and have discover that on the laptop it is a lucent modem i also have the instructons up to that point in Q4... at one stage the modem was working then when i switched it off and on the next day...it didnt work...configuring and setting up isnt as easy as windows so i need to be taught...HELP HELP HELP :confused: :confused: :confused:

---

### Post by Dr. Nick on 2006-06-14
to answer no 1 you can use samba, their are multiple howto's here already.

You can use laptop network cards aswell.

 If you dont mind me asking, is thier any way you can get 6.04 dapper instead of hoary release, some of the problems you have may already be fixed in the new release, or atleast more people who are able to help out.

---

### Post by Arnaud_B on 2006-06-14
Hi,
I'm not sure of how much help I can be but I gonna give it a try... :-)
> 
(1) can i link up my laptop (ubuntu box) with my pc (XP box) via network cards and cable

Do you mean you want to set up a local network between a ubuntu and a windows machine? like for sharing files and printers?
if yes for sharing files with a windows machine you need to set up samba but this is done by default during the installation so you shouldn't have to worry... at least for me this worked out of the box... (you first need to set up network on the windows machine of course then you'll see the windows shares from ubuntu when typing smb:/ in your file manager...)
and for network printing this depends on which machine is connected to the printer... check [https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu)

> 
(2) hook up to the net on my laptop

meaning you want to connect to the internet with your laptop? well sure you can... depends if you want to plug or setup a wireless connection... the first case should work out of the box... for wireless connections it depends very much on your card, mine was working out of the box but this can be more difficult with other cards I guess... 
lscpi tells you what hardware you have (detected one...not modems usually)
ifconfig tells you which interface your wired connection use 
iwconfig tells you which interface your wireless connection use (if you need to connect to a WPA network you need to have the code with you of course...
then you bring the interface up using ifup <interface_name> or down with ifdown <interface_name>
(replace interface_name with eth0, eth1, wlan0 or anything else appropriate...)

About your last problem of modem I cannot say anything sorry my modem was working too quite easily with alsa... don't know about lucent stuff...

Hope this helps,
Good luck!
A.

PS: you could (well I think you should...) update to ubuntu dapper 6.06 a lot of stuff got improved in terms of hardware supports, drivers, and stability... :-)

---

### Post by adwait on 2006-06-14
1)Yes
2)Yes
3)Use
```

sudo ./<filename>
```

4)
Use
```
sudo vi /etc/udev/......
```

---

### Post by pyromithrandir on 2006-06-14
For number 3 you may actually need to do this in the terminal:
> cd folder-where-the-file-is
chmod +x filename
sudo ./filename

---

### Post by Hentai_Jeff on 2006-06-14
first for the love of god upgrade to dapper, second with samba you can link up to your XP machine

---

### Post by alexohara1 on 2006-06-14
hi Dr nick
i have ordered a copy or two of buntu 6.06lt (i think this version) but am not sure when or if it will be arrive here in AU...it was ordered about a week ago...so ill see by the end of the month
i was going to download it but when i clicked on the download i seen about 30 odd links or partsnot sure) then to download them all and try to manually install them id be lost especially on the linux box....
i have read that the latest release has more detection methods than the previous ones..which is a good deal for the newbies...

*********
would you know if there is a direct download (link)for the whole system?
i couldnt find the iso link....just all the files...
*************

i only have my sad sad XP box working....:(

---

### Post by H.E. Pennypacker on 2006-06-14
> (1) can i link up my laptop (ubuntu box) with my pc (XP box) via network cards and cable

What exactly are you trying to do?  Are you trying to transfer/share files?  If so, you should be able to get that done.

> (2) hook up to the net on my laptop

Why wouldn't you be able to use the Internet?  Did you get the impression that Ubuntu users are devoid of an Internet experience?

> (3) id like to install neatbeans5.1 it is a linux download from java and ends in .bin (id imagine binary format) so how to do this from the terminal window

Did you consider downloading whatever neatbeans is from Synaptic?  It may already be there.

> (4)At this site [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) 
below the heading of Drivers For Lucent Modems or similar...it says this....[To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:] 
so how do i create a file is it mkdir /etc/udev/rules.d or is it done seperatly

Go to Applications > Accessories > Text Editor.  a program called gEdit will open.  There, type whatever you're told to do.  Then save the file in the directory you're told.

> i have been to linmodem.org and have download the modem tool,,, installed it and have discover that on the laptop it is a lucent modem i also have the instructons up to that point in Q4... at one stage the modem was working then when i switched it off and on the next day...it didnt work...configuring and setting up isnt as easy as windows so i need to be taught...HELP HELP HELP 

Are you on dial-up?  Assuming your hardware is detected, you should be able to find out the name of modem.  Second, first try using the search feature by seeing if there are other people in the same position.  If you do find others, use whatever solution they provide.

Lastly, why not upgrade to Ubuntu 6.06 (Dapper Drake)?

---

### Post by jason.b.c on 2006-06-14
> hi to all
im only new to linux and ubuntu.

He must also be extremely new to disscusion forums as well , He posted **12** new threads here that are all the same thing...[-X

---

### Post by alexohara1 on 2006-06-14
thanks Arnaud
to question 1
yes this is what id like to do but have failed on a billion attempts
On the xp box iset it up thru the wizard and use computer to computer connection...but on ubuntu 5.04 im setting it up thru System>>Administration>>Network Settings....
i have a little icon there with ethO but not sure to see if connection is made on either end..
to question2
i already have connected the laptop(ubuntu box) to the internet but how i done it i have no idea i was following about 5 different sets of instructions at the time but now it doesnt work..it took me about 4 hrs (research and testing) and now im not really in the mood to start again...

so i was hoping on a direct solution... do you know if there is a direct link to the download of the latest version...i did find ubuntu 6.06lt but i seen about 30 links or parts so i didnt now what to do so i left it...
regards alex

---

### Post by loell on 2006-06-14
no. 3 question.. 

yes you can run netbeans 5.1

you can execute a .bin file by

./filename.bin

as with java sdk/jdk installation.. there are lots of past threads about how to install this, do a search in the forum :)

---

### Post by Arnaud_B on 2006-06-14
Hi.
first for downloading dapper click on your country there: [http://www.ubuntu.com/download](http://www.ubuntu.com/download) any of these links will do and there is no several parts.
But if you want to upgrade you just change breezy or hoary depending on what you use to dapper in /etc/apt/sources.list. If you want to do a clean install just download the  iso and reinstall... I could detail more about your problems but if you are about to reinstall it seems a little useless... let me know what you do...
Good luck!
A.

---

### Post by loell on 2006-06-14
no. 4 question

etc/udev/rules.d/10-local.rules

10-local.rules <-- is the file here and
etc/udev/rules.d/ <-- is the directory

 since /etc directory and sub-directories is owned by super user so you need to be root with this command

------>    sudo su

then enter super user password..

then you can edit/ or create 10-local.rules file by

------>  gedit etc/udev/rules.d/10-local.rules

then save whatever you put in there..

---

### Post by simonn on 2006-06-14
[QUOTE=alexohara1]
(1) can i link up my laptop (ubuntu box) with my pc (XP box) via network cards and cable
[/quote]

Yes, but I am sure you meant to ask more than this?

[http://linuxmafia.com/faq/Essays/smart-questions.html](http://linuxmafia.com/faq/Essays/smart-questions.html)

> 
(2) hook up to the net on my laptop


Yes, but I am sure you meant to ask more than this?

> 
(3) id like to install neatbeans5.1 it is a linux download from java and ends in .bin (id imagine binary format) so how to do this from the terminal window


```

$ chmod +x [path to file]
$ [path to file]

```

The chmod +x makes it executable and then you run it. Linux, by default, does not consider your current directory to be in the path, so you may have to preceed a command with ./ if it is in the current directory and the current directory is not in the path.

> 
(4)At this site [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) 
below the heading of Drivers For Lucent Modems or similar...it says this....[To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:] 
so how do i create a file is it mkdir /etc/udev/rules.d or is it done seperatly


With a text editor e.g. gedit, nano etc.

> 
Finally, please if you have the answers...make sure there simple step by step guides...im still a dummy to this system but id like to give it a go....


Install rute.

It is in the multiverse repository as rutebook or read it here [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz).

---

### Post by alexohara1 on 2006-06-14
thanks adwait...
im having troubles on all aspects...
 in response...
(1) On the XP box i used the wizard and set it up as a computer to computer connection and on the ubuntu box i was setting it up via the network settings theres an icon there with eth0 but is there any way i can test if the are talking to each other... in Places>>Network Servers i have an icon called windows network but when i click on that a blank window appears??
(2) i already hooked the laptop(ubuntu box) up to the net but today i have no connection no nothing and it took me about 4 hrs (researching and testing) so i have no idea how i really got it to work and really i dont fill like starting again...i was hoping for an easier approach...
(3)ok i tried this and the java file does some checking and returns nothing so it could be a problem on java's side or the system still isnt correctly configured...so you can install prg either by ./<filename> or  what about apt-get install <filename>
(4) i type that with the whole file name and it took me to a notepad like screen so i entered what they ask but couldnt save it so i just click the x and exit...dont know what this was??

---

### Post by alexohara1 on 2006-06-14
thanks pyro....

i followed that... thats to change the permission settings (read, write, execute)
thank anyway slowly but surly i will get this all togetther
regards alex

---

### Post by adwait on 2006-06-14
Oh, I forgot that you have never used linux before. For no 4 try usinhg
```
sudo gedit /etc/udev.../
```

For the java file, maybe jre isnt installed on your system?? Try
```
sudo apt-get install sun-java5-bin
sudo apt-get install sun-java5-jre
```

About the networking, not really sure about the exact procedures.

---

### Post by alexohara1 on 2006-06-14
thanks guys
yes i think an upgrade is definetly on the list...
and jason... did i make a mistake posting the same message in different sections ... i wasnt sure exactly where to place them, as my questions covers:- hardware, application support, desktop support, installation help, networking support and laptop support....basically im looking for HELP on detecting my HARDWARE(modem), and being a new user to ubuntu im new to the enviroment of the APPLICATION and its surroundings, so since im using the DESKTOP version and not the SERVER version of the APPLICATION, i wasnt 100% sure on the INSTALLATION methods for either modem connection or NETWORKING the system on my LAPTOP....
however i did place them all under hoary 5.04 so at least i got that right...lol 

regards alex

---

### Post by alexohara1 on 2006-06-14
brilliant loell
but i get a return message of "could not save the file "/home/alex/etc/udev/rules.d/10-local.rules"

sta je?

i checked on a fresh install that linux-restricted-modules-2.6.10-5-386
was installed and it was....ok (this is supposed to have the lucent drivers there.........)
then in the terminal i must type ...
$ sudo sh -c "echo lt_serial >> /etc/modules"
  $ sudo sh -c "echo lt_modem >> /etc/modules"
so do i did....
now i must create the file ....
/etc/udev/rules.d/10-local.rules
and in that file i must put ...........
#ltmodem 
  KERNEL="ttyLTM0", SYMLINK="modem"
then it says i must now load the drivers as such...
$ sudo modprobe lt_serial
  $ sudo modprobe lt_modem
i have used the modem tool from linmodem.org and it says that i have a lucent winmodem so if i follow this procudures from [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)
nothing works....
and add your section of code....it says i cant save it...
shit... i think i must upgrade everyone on this forum really doesnt have an answer why or how to...ok they think they have they howto's section but whats going on i follow it and it dont happen...perhaps its not detailed enough or they just have moved on to 6.06.....

kako sranje...
hell can u help?

---

### Post by loell on 2006-06-14
hi again, :) 

the /etc is not a subdirectory for /home directory its actually separate..

so, click on the terminal icon and the terminal will show..

then do 

------>   cd /etc

then you will be in the /etc directory, then do

------>  cd udev

then do 

-----> ls

then you could see these files

------>   rules.d , udev.conf

the you need to be super user to  create "10-local.rules" file
then you do

-----> sudo gedit 10-local.rules

then it will open, and you can edit and save it.. :)

---

### Post by alexohara1 on 2006-06-14
thanks to everyone for all the help...
i have managed to perform all the task without errors from [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)
under the heading for lucent modems...

but things stilll dont work i have tried to  configure the network settings and dial in... and i get this error.. "could not enable the interface ppp0" and it goes on to say check that the settings are apropriate for this network and that the computer is correctly connected to it...

everything looks fine with the setting.... the only thing which doesnt work is the autodetect feature, which it cant autodetect the modem device...

so i must be missing something outside of those steps...
anyhow ive giving up for now...and am going for the latest version download

perhaps in a few months or so after following linux ill be able master the system...but for now its important i get this laptop up n running correctly as i use it for work so ill try the new version of ubuntu if i still cant get it going(net and networking) ill jump back to XP then try again later when im not so busy.....

---

