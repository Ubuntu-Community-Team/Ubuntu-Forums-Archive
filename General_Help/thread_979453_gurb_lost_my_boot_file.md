---
title: "gurb lost my boot file?"
date: 2008-11-12
forum: General Help
---

### Post by jackechanprime on 2008-11-12
ok, total nub here so bear with me. need technical terminal help, or someone who knows how grub works. this happened with the 8.10 ubuntu update, after the install was complete the computer restarted, as per the instructions. grub loaded... and... nothing else happened. i restarted my computer several times, and it still sticks at this screen. i can log in via command line by pressing alt+f4 and entering username/password. I'm thinking that if this bug isn't 'fixable' then I'm just gonna get my data off and reinstall ubuntu. but now, note the noobness, i cant get the external drive to mount, let alone find it afterward to move the data into it. it's a flash drive, so i know that means i have to deal with a file called 'sda1' whatever that is. i honestly have noooooo clue what i'm doing. this is like... lv 20 computer stuff, and i'm a measily lv 5 geek, so... HELP!! need to know how to mount a drive, transfer data to it, and un-mount it, or simply figure out wtf is wrong with grub.

thank you... anyone!!
jack_e_chan
:confused:

---

### Post by cariboo on 2008-11-12
Have you tried starting in recovery mode and once at the menu choose **xfix** this will create a new /etc/X11/xrog.cong and should get you up and running in at least low resolution. Once xfix is finished just choose continue from the menu. 

Linux doesn't just C,D,E drive letters like windows does, it uses devices eg: /dev/sda1 means the first partiton of the first hard drive.

Jim

---

### Post by jackechanprime on 2008-11-13
ooooh... erm... well, then sda1 certainly seems unhelpful then. :/

ok... well, that throws just about anything i knew about how to mount a drive on ubuntu out the window... not that it was that much anyway...

ehh... sorry for the noobness here... but the thing isn't showing the option to go into recovery mode. i donno if this is because the systems messed up... or i just don't know what I'm doing, but all that happens is the Compaq (it's a compaq presario c700 btw, if that's at all helpful) logo comes up with a bunch of F(whatever) options that lead into bios stuff, then grub loads, and nothing else happens.

i tried using a live cd, only to discover that it doesn't present that option either. soo... i'm back to square one, not knowing how to mount a usb flash drive in terminal, and wondering what it's directory will show up as so i can *cp* stuff into into it, then probably reinstalling. that is, unless someone knows how i get my computer to un-mess itself up.

plz, plz, plz, plz, plz, anyone help~!
jack

P.S.
oh, and thanks for the help cariboo907.

---

### Post by jackechanprime on 2008-11-15
bump

---

### Post by rbmorse on 2008-11-16
Let's fix GRUB so the machine boots. 

Put the ubuntu installation CD in the machine and boot from that.  Select "run ubuntu without making any changes to your computer" from the boot menu.

When the machine is running from the Ubuntu desktop, click accessories, click on terminal.  A "dos box" will open.  At the prompt in the terminal window:

sudo grub
find /boot/grub/stage1

That will return a result that looks like this:

(hdX,Y)

where X and Y are integers.  Note the X and Y values. 

Type the following in the terminal very carefully. do not type anything that follows the "#" character -- it's a comment to help you

root (hdX,Y)      #<----  where X and Y are the values returned above
setup (hd0)       #<---- where "0" is the number zero

You should see several lines of technobabble and then be returned to the GRUB prompt.  

quit
exit

That will close the terminal window and return you to the Ubuntu desktop. From there click on "system" the "quit" then "restart" to reboot the machine. Remove the CD from the drive when prompted.  

When the machine starts, it should present the GRUB menu, or if Ubuntu is the only O/S on the machine, it may just go straight to Ubuntu without intervention.

---

### Post by jackechanprime on 2008-11-17
ok... this cant be good...


looks like the grub file wasn't lost at all. it was there the whole time... it just isn't doing anything. i obviously don't know whats wrong with it, as i hardly even know what it is. even after following the instructions as above to the letter, and with no errors coming back, the system still isn't booting into the gui. i keep getting stuff about a 'gnome display manager'... whatever that is. i can push alt+f4 to get into CLI and log into terminal... but since i'm useless at terminal, i'm still at square one.

...help?
jack

---

### Post by jackechanprime on 2008-11-18
bump

---

### Post by HousieMousie2 on 2008-11-18
Try this?

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by jackechanprime on 2008-11-19
hmm. that looks like pretty much the same thing i already tried. i don't have multiple partitions or anything, so grub was at (0,0). i did all the stuff to make grub use that, but even now that it's using it, nothing is happening --still--. so far as i can tell, my drive is fully recognized, so forcing a new root directory in would seem more likely to mess things up... right?

i honestly don't know what i'm up against here. anyone who does know or have even an inkling of whats wrong with my computer, please help?

just to recap, the problem was generated by attempting to upgrade to ubuntu 8.10 (which was an option provided in the little 'there are new updates for your computer' thingy in the top right.) the download was a little rough, since my bandwith that day was going nuts, so the dl stopped and started several times over 2 days, but it didn't say anything about corrupted files or anything, so i just let it do it's thing. when it finally downloaded everything, it took forever looking through my file directory for 'outdated packages' removed seemingly every program on my drive, then prompted to restart. when it did so it froze on the 'running local boot scripts' screen. i restarted it manually (power switch), and it did it again, and again... and stays there to this day. it looks to me like it isn't a problem with grub anymore... more like a problem with... everything else.

i'm really to the point of just wanting to get the data off the machine and trashing the busted install, but if someone can help me 'unbust' it, please help... or please tell me how to mount a usb flash drive and get my stuff onto it.

thanks for anything!
jack

---

### Post by bodhi.zazen on 2008-11-19
Did you consider booting a live CD, mounting your Ubuntu partition, and seeing what is on it exactly ?

---

### Post by jackechanprime on 2008-11-21
errr... i can do that?

how? (sure i consider it now that i know about it)

---

### Post by bodhi.zazen on 2008-11-22
boot the live CD

Open a terminal 

```
mount /dev/sdxy /mnt
```

Where /dev/sdxy = your ubuntu partition (/dev/sda1)

Then ```
gksu nautilus /mnt
```

When you are done, unmount the first partiton and go to the next ...

```
sudo umount /mnt
sudo mount /dev/sd_the_next /mnt
```

and on ...

---

### Post by jackechanprime on 2008-11-22
ok... i'll try it. erm... how do i know which partitions i have and what theyre called? i'm guessing alpha/numeric starting at a/1, so i'll just poke around try a/1, a/2, b/1, b/2... see if the comp shouts at me or not... :/

not sure how to 'look in them' either, hoping that makes itself self-evident.

(typed this all while the comp was booting from the cd... so we'll see how it goes)

--update.

erm, well there's something there that wasn't there before. while my home folder still shows nothing but 'ubuntu' when i cd all the way up i find something in red print with a black/grey background: 'initrd.img' i've never seen that before, and dont know what it is. gonna try 'a/2' now, see what happens.

--update v.2

well... 'a/2' asked me something about specifying a file type, donno enough about that to know that i dont know, and 'b/1' and 'b/2' are apparently 'special devices' that 'don't exist' so... yeah... i donno if i found out anything usefull at all here, but i'm sure you all found out just how little i know >_>

thank you so much for helping/tolerating me!
jack

---

### Post by bodhi.zazen on 2008-11-22
No problem.

Take a look at this link :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Once you are finished looking at a partition, unmount it before mounting the next.

```
sudo umount /mnt
```

Note only i "n" in umount

---

### Post by jackechanprime on 2008-11-24
ok. i read the guide, but... how do i know how many partitions i have? as far as i knew it was '1' but now, according to your guide there's at least 5? so... which ones which? and thanks, i'll try to remember to unmount. i think i was, but i cant be sure.

so... now that i know enough to know that i dont know... can you tell me what i dont know? lol... >_> i'm being a major headache arnt i? well, thank you for all your help!!!

thank you
jack

---

### Post by bodhi.zazen on 2008-11-24
With the live CD you can see your hard drives graphically with gparted.

From the command line with :
```
sudo fdisk -l
```

---

### Post by jerrykenny on 2008-11-24
Are you guys sure this is a boot problem ?   looks as if the system is booting . . . .but gdm isnt starting.

Also with the grub splashscreen (which i think is most distracting) is hiding any sort of feedback at all .

---

### Post by jerrykenny on 2008-11-24
Jackie, if you think that the above is true . . . . try pressing "e" at the grub prompt . . . at the next line line press "e" again, . . . and delete the word splash" if you can, . . . then hit enter, and then "b" for boot.

If the system IS ACTUALLY booting then you might get some usefull information.

You might then try 

sudo killall gdm
sudo dpkg-reconfigure xserver-xorg
sudo gdm

---

### Post by jackechanprime on 2008-11-24
erm... no clue what the grub prompt is, all i can get into is a CLI full screen terminal. before that, the computer is not even recognizing that i'm telling it anything, almost as if i'm in a word processor, but formatted to look like a CLI.

while poking around to find the 'grub prompt' i DID find something though. the 'grub is loading...' screen, i pressed esc, and discovered that i am apparently running one of these:
        -- ubuntu 8.04.1, kernel 2.6.24-21-generic
        --          "           "        "   "    (recovery mode)
        -- "          "       "  2.6.24-19-generic
        --     "        "            "       "    (recovery mode)
        -- "          "  , memtest86+

but if i select one of the a whooooole lot of stuff scrolls by and at the end of it all, i'm still left in CLI, after logging in... in CLI...

hmm... odd... 'whoami' is coming back with root, with no password input? i donno if that's normal or not...

anyway here's the exact screen text i'm looking at when my system 'finishes booting up'

*starting anac (h) ronistic cron anacron                    [ok]
*starting defered execution scheduler atd                   [ok]
*starting periodic command scheduler crond                 [ok]  
*checking battery state...                                  [ok]
*running local boot scripts (/ect/rc.local)                 [ok]
_

^^ that's a blinking cursor there. i can type anything through that and not get so much as a command not found back.

if i press alt+f4 i get this screen:

ubuntu 8.10 workbook-1 tty4

workbook-1 login: _
                  
                  ^^ again another cursor. this gets me into a CLI. gonna try that live cd thing u posted now zazen, back in a sec with results (i hope)

---

### Post by jackechanprime on 2008-11-24
ok, looks lime sda1 is my boot partition, sda2 is all my stuff, and sda5 is 'swapspace' nothing else to report. i tried again to mount them, but all o got back was 'mount: you must specify the filesystem type' i donno if i'm doing something wrong or not... but... well, that's what i'm getting and i'm typeing what you told me to verbatim.

thank you for your continued help!!!
jack

---

### Post by jackechanprime on 2008-12-01
bump!

happy thanksgiving all! i just got back from being out of town.

:[ no one's responded yet...

i hope you were all having good food too!

>_> and not just walking away cause i dont know what i'm doing...

thank you far any help!!

jack

---

### Post by bodhi.zazen on 2008-12-01
> **jackechanprime said:**
> erm... no clue what the grub prompt is, all i can get into is a CLI full screen terminal. before that, the computer is not even recognizing that i'm telling it anything, almost as if i'm in a word processor, but formatted to look like a CLI.

while poking around to find the 'grub prompt' i DID find something though. the 'grub is loading...' screen, i pressed esc, and discovered that i am apparently running one of these:
        -- ubuntu 8.04.1, kernel 2.6.24-21-generic
        --          "           "        "   "    (recovery mode)
        -- "          "       "  2.6.24-19-generic
        --     "        "            "       "    (recovery mode)
        -- "          "  , memtest86+

but if i select one of the a whooooole lot of stuff scrolls by and at the end of it all, i'm still left in CLI, after logging in... in CLI...

hmm... odd... 'whoami' is coming back with root, with no password input? i donno if that's normal or not...

anyway here's the exact screen text i'm looking at when my system 'finishes booting up'

*starting anac (h) ronistic cron anacron                    [ok]
*starting defered execution scheduler atd                   [ok]
*starting periodic command scheduler crond                 [ok]  
*checking battery state...                                  [ok]
*running local boot scripts (/ect/rc.local)                 [ok]
_

^^ that's a blinking cursor there. i can type anything through that and not get so much as a command not found back.

if i press alt+f4 i get this screen:

ubuntu 8.10 workbook-1 tty4

workbook-1 login: _
                  
                  ^^ again another cursor. this gets me into a CLI. gonna try that live cd thing u posted now zazen, back in a sec with results (i hope)

Now that sounds as if your system is booting just fine, so I do not think it is a problem with grub, but rather a problem with X.

Boot to recovery mode and select teh "XFIX" option -> re-boot.

If that fails, what videocard do you have ? (I suspect nvidia or ati).

---

### Post by jackechanprime on 2008-12-01
erm, ok, i chose the first recovery option, but still no gui to speak of, it just went directly into CLI, with a WHOLE lot of stuff streaming by. last thing it came up with was:

* monuting local filesystems... [ok]
*activating swapfile swap... [ok]
* checking minimum space in /tmp... [ok]
* skipping firewall: ufw (not enabled)... [ok]
*configuring network interfaces... [ok]
* setting up counsole font keymap... [ok]
root@workbook-1:~# _

--again with the CLI cursor. if this was supposed to happen, then woopie, if not... >:[ not woopie. either way, i dont think your phrasoligy of 'select xfix' was ment to translate into 'type it into cli' so, i'm gonna try the other recovery mode b4 doing that.

---

### Post by jackechanprime on 2008-12-01
@_@ oh poopshoot.

the second (recovery mode) tab came back with this:

error 15: file not found

press any key to continue...

--erm... not good?

gonna try 'xfix' in the other mode and see what the computer spits at me.

well, creatively enough 'xfix' came back with 'command not found'.

back to you .zazin!
thank you infinately for all your help!
jack

---

### Post by jackechanprime on 2008-12-01
oh, and, erm, i donno what video card i have. how do i find out? (turns laptop over and starts looking at the stickers)

---

### Post by jackechanprime on 2008-12-02
bumpity-bump.

---

### Post by jackechanprime on 2008-12-03
bump for the night

---

### Post by bodhi.zazen on 2008-12-03
When you boot to recovery mode you should get a menu of options. One option is to start a command line. One option is XFIX.

If you do not see XFIX, start a command line and enter

```
dpkg-reconfigure xserver-xorg
```

Then reboot.

---

### Post by jackechanprime on 2008-12-03
erg!

still no gold .zazen. i managed to blunder my way through what was apparently the process of redefining my keyboard, and told it to reboot, but to no avail. it's still stuck on the same screen after 'booting'.

please tell me you still have more cards up your sleeves?
thank you!
jack

---

### Post by bodhi.zazen on 2008-12-03
It depends on your videocard, nvidia or ati -> go with Envy.

Envy can be downloaded and run from the command line :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Tenyuu on 2008-12-03
thanks a lot! now I got GRUB back, (I posted somewhere i needed help with a problem like this, couldn't find it to check 4 a reply.):D

---

### Post by bodhi.zazen on 2008-12-03
it is GDM (GDM is the graphical log in screen, GRUB is the boot manager).

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jackechanprime on 2008-12-03
erm... ok... now, sorry about this, but could you tell me just how to download/run that in cli? i didn't even know my internet was connected when i'm down in cli... er, yeah, sorry, total noob moment, but, thank you!!

jack

---

### Post by bodhi.zazen on 2008-12-03
The easy way, envy is in the repos :

```
sudo apt-get install envyng-core
sudo envyng -t
```

You do not need the sudo if you are doing this from the recovery mode.

---

### Post by jackechanprime on 2008-12-04
i got this back... just as i feared...

reading package list... done
building dependency tree
reading state information... done
E: couldn't find package envy-core

>_<

i donno what this means, but... something ain't working.

thanks
jack

p.s. lol, it's good to know that this has helped someone!

---

### Post by bodhi.zazen on 2008-12-04
you have to enable some repositories.

Open /etc/apt/sources.list

```
nano /etc/apt/sources.list
```

Scroll down to the bottom and remove the octothorpe (#) in the front of the universe and multiverse repos.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

(normally you would do this :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) )

Then, update your system :

```
apt-get update && apt-get upgrade
```

and finally install

```
sudo apt-get install envyng-core
sudo envyng -t
```

---

### Post by jackechanprime on 2008-12-04
erm... theirs nothing to do... the nano command came up with a fairly literally blank screen. 

{top of screen}
gnu nano 2.0.7           file: /ect/apt/sourses.list




[absolutely blank]





[all sorts of little command thingy's down here]
{bottom of screen}

and... erm... what an octothrope?

i read through the page... but have immerged more confused than before. i've never touched nano b4, and i dont know anything about repository's (except that they apparently exist)

ok, yeah, after about 20 minutes of fiddling around, i've come to the conclusion that i have absolutely no idea what i'm doing...

help much?
jack

---

### Post by bodhi.zazen on 2008-12-04
you have a spelling error. 

```
nano /etc/apt/sources.list
```

not

/ect/apt/sour**s**es.list

octothrope, love that word :twisted:

# comments start with a hash
# so you need to simply remove a few # from a few lines is all

you can navigate in nano with the arrow keys. nano also has built in help, at the bottom of the screen. 

See "^G Get Help" ^ is short hand for the control key.

so hit ctrl-g (it does not have to be a cap G).

Anyway , remove a few # , ^x to exit, type "Y" to save :)

---

### Post by jackechanprime on 2008-12-05
oops. i think that might have just been a transcription error on my part. donno, checking/retrying now.

yeah, looks like i had it right the first time just said it wrong on the blog. this time it came up (after very carefully typing it in to remove spelling errors) with a little [new file] right above the toolbar at the bottom.

... and i tried that help command before, but, and i must say whoever engineered nano has a good sense of humor, cause it kept telling me to 'be reasonable' and once even 'mumble, mumble' 'd at me.

... that was about the time i decided i didn't know what i was doing and to ask you...

either way, this file is totally blank... from what your saying... that shouldn't be the case?

thank you for helping!
jack

---

### Post by bodhi.zazen on 2008-12-05
blank file == typo

You can use tab completion to reduce errors (you have a few in your posts which is confusing me as i myke ltos of ytpos too).

nano /et<tab>apt/so<tab>

make sure you are running as root or you will have to use sudo :twisted:

---

### Post by jackechanprime on 2008-12-05
ok, trying again...

0.0

that little smiley is starting to get scary...

ok EXACT transcription of my input (triple checked for accuracy):

sudo nano /ect/apt/sources.list

and i got the same blank new file thing out. when i tried to tab in the entry, the computer just beeped angrily back at me, the little 'no-can-do' beep. then when i tried to exit, it prompted me to save changes, and i tried to, only to be told that it is unable to because the directory doesn't exist!

O_O

not good?
jack

(oh, and sorry for my previous typos, i can be messy when i'm in a hurry, i'll try to cut down on them in the future. thank you so much for helping!!!)

---

### Post by bodhi.zazen on 2008-12-05
:lolflag:

you are not using tab completion :)

[size=6]/etc/apt/sources.list[/size]

you have ect 

blank file == typo

---

### Post by jackechanprime on 2008-12-06
oh... i am soooooooooooo stupid...

uses 'ls'

riiiight... wrong directory.

cd .. (3 times)

tires again.

>_< major narb moment.

well, at least we know that THAT was the problem. dont have time to try right now, have to be at work in like, 15 minutes. this came to me in an appiphiny (however you spell that) in the shower this morning. be back tonight to try it right!!!

thank you so much for putting up with my idiocy!!
jack!

---

### Post by jackechanprime on 2008-12-06
GOT IT!!!

ok, i figured it out, i think. i deleted the '#' 's in front of all the lines that started with 'deb' and ended with a http line of some sort. i hope this works!

---

### Post by jackechanprime on 2008-12-06
okaaay... now problem (you are really starting to love me at this point, i'm sensing...)

i deleted all the comment # things like you told me to, then tried to download the evny-core thing, but again it said not found. i looked back and saw you had said to update my system. i tried that... and that's the new problem. i got about 20 -could not resolve 'whatever'.com- messages back.

i'm gonna guess this means that somethings up with the internet connection...

*sigh*
does my computer hate me, or do i just suck at this that bad?
jack

(oh, and yeah, i did check to see if my cord was actually plugged in. >.<)

---

### Post by bodhi.zazen on 2008-12-06
yes, that generally indicates you have a problem with your network.

Try:

(I assume are running as root, otherwise add sudo in the front of the command)

```
/etc/init.d/networking restart
```

---

### Post by jackechanprime on 2008-12-07
done... still didn't work.

getting the same 'could not resolve' thing back.

I'm running dsl through a 'zoom' brand modem. i'm connected via hard-wire (since my wireless didn't work in the first place, but that's not important right now), either way, i donno what's relevant enough to tell you. this has been happening as long as this 'problem' were trying to fix has been going on, if not longer. i just thought that i had to somehow 'force open' my internet ports from cli before i could use them... waaaay oven my head to even think about, which is why i was kinda: 'wait we can use the internet like this?' earlier.

maybe it might be a better idea to go with my first plan, and get my data off of this blasted thing, then just reinstall ubuntu.

thanks, jack

---

### Post by jackechanprime on 2008-12-09
bump.

so are we changing plans to just rescue, or are we still trying to repair the thing? i vouch for just getting the data off, cause this is just taking too long, and i have the inkling feeling that theirs more and more problems waiting for us down the road, so i kinda just wanna cut this hydra off at the knees.

tell me what you think
jack

---

### Post by bodhi.zazen on 2008-12-09
You might try booting an older kernel (should be an older kernel on the grub list).

Otherwise, next step is to fix the network.

Output of :

ifconfig

What happens when you dhclient eth0

---

### Post by jackechanprime on 2008-12-10
you mean the list of options where i can boot into recovery, normal, and two other options that i don't know what they do? those are the 'old kernels' then? if so... problem there. tried those before when you said to try recovery mode, came back with error: file not found.

checking the network now, standby...

ok, output is thus: (whatever it all means)
lo         link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
UP LOOPBACK RUNNING MTU: 16436 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

well that's a lot of zeros... i'm gonna put my noobish skills of deduction to work and say that that means nothing is happening whatsoever?

ok, next thingy...

erm something happened there... hold on...

OMFG THAT DID IT!!!

update in progress!!

erm... what...?
upgrade downloaded a bunch of stuff, but 'sudo aptitude install' is spitting back something weird. i't like, listing the names of everything it downloaded (a good 45 packages) then saying 0 upgrades/installs/removes... and '596 was not upgraded' odd...

oops... well, cant scroll back up to give u exact output of what that dhclient eth0 command did exactly the first time, and it's doing something else now, so i'll give you that instead:
(i think last time i created a 'pid' file, whatever that is. just guessing though)

there is already a pid file /var/run/dhclient.pid with pid 5360
killed old client process, removed PID file
Internet systems consortium DHCP client V3.0.6
Copyright 2004-2007 internet systems consortium.
all rights reserved.
for info please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

listening on LPF/eth0/00:1b:38:ef:24:e6
sending on LPF/eth0/00:1b:38:ef:24:e6
sending on socket/fallback
DHCPREQUEST of 10.0.0.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.7 from 10.0.0.2
bound to 10.0.0.7 --renewal in 34345 seconds.

looks like techno-bable for 'i just connected to the internet' to me.

so... any ideas on why install suddenly decided it hates me?

gonna restart and retry.
think on it in the 10 minutes in which i'm sure you wont even have read this by.

ok, after the reboot the connection is down again. retrying that dhcliant eth0 again.

---

### Post by jackechanprime on 2008-12-10
ok, internet seem to be being restored by that command (hails it as magical)

anyway, i downloaded envy core, and did the -t thing u told me too, and it brought up a list of options for drivers to be installed, donno which one i have, so i'm just gonna do all of em. i can just delete em later right?

other than that, i also did apt-get update && apt-get upgrade
got back a funny error message at the end:
E: could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/), are you root?

well, i'm not actually running root. i er... have long since forgotten what my 'root username' was... >_> one of the reasons i'm so hot on simply reinstalling...

i do know the password though, which is why i've just been sudo-ing everything. this is probably bad, but yeah, cats outta the bag.

well, on to installing drivers!!

ok, that hit a brick wall faster than a cat hot on a mouses tail.

the first driver i tried the 'ATI' one, had only one option, and when i tryed it, it came back with 'error the kernal headers are missing and could not bee installed' i donno if that was verbatim of what it said, but i think you can get the jest from that.

i then tried the NVIDEA (or however you spell it) option, and that had about 5 options, so i just kinda backed away slowly, and shut everything down.

tell me what to do, for you are the master!
jack

(progress makes me very happy <<(^.^)>> )

---

### Post by jackechanprime on 2008-12-10
bump

---

### Post by jackechanprime on 2008-12-12
bump. plz help!

jack.

---

### Post by bodhi.zazen on 2008-12-12
Hard to tell ...

You need to know what card you have (ati or nvidia)

---

### Post by GuitarRocker2562 on 2008-12-13
If you really want to backup your files then it is pretty easy.

sudo mkdir /media/backupdrive

plug-in your harddrive, should be /dev/sdb1

sudo mount /dev/sdb1 /media/backupdrive

cd /media/backupdrive

ls

make sure the files listed resemble what would be on that drive, if not, let me know.

sudo mkdir /media/originaldrive

sudo mount /dev/sda1 /media/originaldrive

cd /media/originaldrive

ls

make sure the files listed seem to be what was originaly on your ubuntu / folder

cd /media/originaldrive/home/USERNAME/

USERNAME should be your ubuntu username

cp ./* /media/backupdrive/Ubuntu_Backup/

cd /media/backupdrive/Ubutnu_Backup/

ls

make sure that all your files backed up (only your user files will have been backed up, to backup your whole drive, sudo cp /media/originaldrive /media/backupdrive/Ubuntu_Backup)

reinstall

---

### Post by jackechanprime on 2008-12-14
i think i'll peruse both avenues for now (since i dont have the time to do either at this moment). now that i know what to do i'll pull my files at the first opportunity, then reinstall,. if we can fix the system before that, then i'll be happy as all hell, if not, then it's going the way of last-weeks leftovers.

on the note of trying to fix the system, i dont know what type of video card i have, nor how to find out. if you know how i'd determine this, let me know so i can do it and get back to you.

thanks!!
jack

---

### Post by bodhi.zazen on 2008-12-14
Well, this is the first step , determine what hardware you have.

```
lshw > hardware.txt
```

If you are not root, use sudo for that command.

Then view hardware.txt with any text editor, or from the command line:

```
less hardware.txt
```

---

### Post by jackechanprime on 2008-12-14
ok, in response to .zazen,

i ran it no problem, but the list didn't include any 'video card' listings. there were 2 things under *-pci that look like the most relevant things there.

*-display:0 UNCLAIMED
description: VGA compatable controller
product: Mobile GM965/GL960 Integrated Graphics Controller
vendor: Intel corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 03
width: 64 bits
clock: 33MHz
Capability: msi pm vga_controller bus_master cap_list
configuration: latency=0

and this one which was the next down:

*-display:1 UNCLAIMED
description: display controller
product: mobile GM965/GL960 Integrated Graphics Controller
vendor: Intel corporation
Physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 64 bits
click: 33MHz
capabilities: pm bus_master cap_list
configuration: latancy=0

everything else was stuff like, the CPU, the hard drive, the usp ports, audio device... etc, etc...

so, looks like (if this is right) i've got something from intel.

...so...

what's that mean? i've got a buggy intel card or something?

thanks for the help!
jack

---

### Post by jackechanprime on 2008-12-14
in responce to Rocker:

woah... when i plugged in the drive this came up:

[54.428833] sd 5:0:0:0: [sdb] assuming drive cache: write through
[54.432462] sd 5:0:0:0: [sdb] assuming drive cache: write through

i'm gonna guess this is telling me... it's on 'sdb5'? i'll see which of them makes the computer angry with me. should be a relatively definitive way to find out.

--
You were right, it was sdb1. all was proceeding fine till i got to the 'CP' part. you didn't specify a destination... and i don't wanna just stab at one when your pretty much leading me around blindfolded.

also to make things simpler, i have all my 'valuable' data in one spot.

home/USERNAME/Desktop/stuff

that folder contains the only stuff on the system i care about, hence is all i want to get off. it looks like your trying to get me to backup the whole system (which is a. why i dont want to 'just take a stab at it' and b. more than a measly 512 thumb drive (my only 'temporary hard drive') can fit.) if we can just somehow surgically remove that, I'd be happy.

oh... hold on.. you did give me a destination. theres a space after the '*' woops. well, still, i doubt it'll all fit on this thing, but i'll try.

--
O_O

it worked.

checking data on another computer before reinstalling...

--
>_< it didn't work.

there's nothing on the drive.

i donno what happened...
jack

---

### Post by bodhi.zazen on 2008-12-14
You have an Intel integrated graphics card.

See: [http://www.google.com/search?q=ubuntu+GM965%2FGL960&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+GM965%2FGL960&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by jackechanprime on 2008-12-15
....ooookay...

so... whats compiz? and... why was it working just hunky-dory before i installed 8.10?

:confused:
jack

---

### Post by jackechanprime on 2008-12-16
bump for zazen and rocker!

---

### Post by bodhi.zazen on 2008-12-16
compiz is your window manager.

I think the problem is with your video card and 8.10, some of the links should suggest a solution (I hope).

---

### Post by jackechanprime on 2008-12-17
your hope in the world seems misplaced here .zazen ... either i'm staring the solution in the face and not recognizing it, or all this stuff is pretty much irrelevant to my problem. something about about stripping out compiz was pretty much the most relevant thing i could find... and that would just exacerbate the problem wouldn't it?

long story short... i cant make heads or tails of any of the stuff that search turned up.

sorry if that makes this more of a hastle, i really am trying here...

jack

---

### Post by bodhi.zazen on 2008-12-17
Basically, 8.10 does not support your video card.

You can either downgrade, ie re-install 8.04 (back up and restore your data) or you can try to download and install the drivers.

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

I have not installed these drivers and if you are still without an internet connection you will have a hard time.

---

### Post by jackechanprime on 2008-12-19
internet is up. you actually figured it out, on of the things you had me try. soooo, then, to backing up my data. i tried rockers directions, and something went wrong. all i have is a 512MB little flash drive, and i only want certain files that i noted in a post 3 or so back, so, if we can get those off i will -GLADLY- reinstall ubuntu (some older version) and start from square 1. i've tried dealing with 'out of the box' drivers before, when i was trying to get my aetheros wi-fi card working... which i never did, and i NEVER want to go through that again, so i think we might just be better off salvaging what we can, then scrapping the install. rest assured, there will be no lost love on my end when it goes (assuming we can get my data off).

thank you!!!
jack

---

### Post by jackechanprime on 2008-12-20
bump

---

### Post by jackechanprime on 2008-12-21
double bump

---

### Post by bodhi.zazen on 2008-12-21
bump ?

You will need to copy your data to an external drive / flash / dvd and re-install

Or you can try to install the drivers.

---

### Post by jackechanprime on 2008-12-21
yeeeah.... thats the problem zazan... i dont know how. i have the flash drive, (a 512mb usb flash drive), and i know where the data is, and i know i will have to use the copy paste (cp) command. what i dont know is how-to/if-i-even-need-to mount the drive, what the destination folder will be, and anything else in between that i dont even know exists yet. if i knew how to do this... this thread would have been over a loooooooong time ago.

thanks
jack

---

### Post by bodhi.zazen on 2008-12-21
Most of the data you will want to save should then be in your home directory. Things like music or other personal data.

Your flash drive should auto mount , just copy over what you will.

If you have nothing special, then go ahead and re-install ;)

---

### Post by jackechanprime on 2008-12-22
ok, that's cool, but... i'd still rather be safe and make sure i'm doing everything right by you. the data i want off of my system is in directory:
home/USERNAME/Desktop/stuff

(i was smart enough to keep everything i care about in one folder, and yes it is whimsically named 'stuff')

so, what i'm gonna do is: sudo CP /home/USERNAME/Desktop/Stuff {no clue}

what's the destination gonna be?

thanks!!
jack

---

### Post by bodhi.zazen on 2008-12-22
Usually flash drives are automatically mounted in /media

/media/disk perhaps

cp -R /home/USERNAME/Desktop/Stuff /media/disk

---

### Post by jackechanprime on 2008-12-22
tytytytyty!!

trying now...

jack

--
*sigh* no gold... as usual...

wherever it's mounting at, it isn't in the 'media' file, or, if it is it isn't showing up as a file or anything at all for that matter. the contents of 'media' are identical before and after plugging in the drive.

when i plug it in i get these 2 lines though:
[265.113344] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[265.116836] sd 6:0:0:0: [sdb] Assuming drive cache: write through 

I'm hoping there's directions somewhere in there?

jack

---

### Post by bodhi.zazen on 2008-12-22
Try :

```
sudo mkdir /media/usb

sudo mount /dev/sdb1 /media/usb
```

You will need to use sudo to copy as well.

---

### Post by jackechanprime on 2008-12-23
hahahha... cool. i thought so. there's already 2 folders in 'media' one called 'usb_drive' the other called 'usb_dripve' <= that one must have been a typo from an earlier attempt. ill just try mounting it to 'usb_drive' then and see what comes of it?

oh, wait nvm... theres already stuff in those folders. i think i should just delete those...
(yes they were there b4 i even plugged the drive in)

trying it your way!!

jack

---

### Post by jackechanprime on 2008-12-23
O...M...F...G...


thank... you...


THANK YOU!!!

it worked!!!

one more question!!

how do i give you one of those little 'thank yous' for your profile!!

you deserve about 200 of em for this!!!!!

thank you so much!!!

jack

---

### Post by bodhi.zazen on 2008-12-23
> **jackechanprime said:**
> O...M...F...G...


thank... you...


THANK YOU!!!

it worked!!!

one more question!!

how do i give you one of those little 'thank yous' for your profile!!

you deserve about 200 of em for this!!!!!

thank you so much!!!

jack


:guitar: 

w00t !

You may need to copy those files back as root then use chown and chmod to change ownership back to you user. If you need help just ask ;)

The thanks button is on the lower right of a post, but please do not feel obligated to thank me, at least not until you have a working system and have restored from back up.

---

### Post by jackechanprime on 2008-12-23
you... may regret the 'if you have any more questions part' there... lol

system is up and running all fine. i've got the data backed up 5 ways so that i'll never have to go through this again, and i know how to use chmod fine, so no problems on that front.

buuuut...

my wireless card isn't working.

this is a loooong standing problem, and i've looked for help on the matter before, and gotten many dead ends, but that was 6 months ago, time to give it another shot and see (and hope) that something out there has changed!
heres what i have:

--Compaq Presario C700 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

heres what i dont have:

--a driver for it.

tell me if you know anything helpful!!

jack

---

### Post by bodhi.zazen on 2008-12-23
Congrats :)

I will help if I can ...

You can start here :

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

And here 

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

If that fails I suggest you start a new thread in Networking and Wireless.

---

### Post by jackechanprime on 2008-12-24
>_< well... there i go w/o thinking... i just thanked you for the previous post apparently... O_o i was more along the lines of thinking of thanking you -in general-

anyway to to that per-chance?

(actually reads post now)

lol
jack

---

### Post by jackechanprime on 2008-12-24
ok, read em now.

erm, i'm no longer running 8.10 for... obvious... reasons,

i'm back to... erm... whatever im running now. (installed via old live cd (whatever was current b4 8.10), and received 223 updates, so i have no clue what i'm actually running(hardy heron of some form or another), all i know is i have a gui now and i'm happy!)

so, the first link i just kinda skipped over.

the second one looks more promising... but... my n00b skills are getting in the way as usual.

i like the '5 rules' bit... but all it left me saying was 'so how do i do xxx' or, 'now if only i knew how to check if i have xxx' and most importantly: 'just how the freck to i manually install something anyway?'

hope your up for the help!
jack

(and just on a side note, i'm havening trouble re-installing java runtime environment, i cant seem to remember how i did it last time, if you can help... plz do so? not... knowing how to actually tell the computer to actually 'install' something isn't helping either. i managed to get a self extracting folder, and i got it to self extract... i think... but Firefox still isn't running it. i think theres something about a 'symbolic link' that i need to do... getting in over my head again here.)

---

