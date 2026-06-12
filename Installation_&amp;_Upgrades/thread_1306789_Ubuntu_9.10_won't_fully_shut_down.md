---
title: "Ubuntu 9.10 won't fully shut down"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by James2k on 2009-10-30
Im new to Ubuntu and only recently began using it as an OS properly so please bare with me on my explaination of my problem. Basically I have a Compaq Presario CQ60-307EA laptop and started using Ubuntu on 9.04 (Not long before Karmic Koala hit the scene) I upgraded from 9.04 to 9.10 but when I read the complete change log I decided I should format and start fresh which I have done with no problem.

The problem I've come across is that when I come to shutdown Ubuntu through the GUI it doesn't fully shut down, what I mean by that is Ubuntu disappears some random text comes up and then my screen goes blank but the laptop doesn't power off just hangs with no screen display showing anything. The power light is still on along with my wireless LED. But the twist to the tale is when I use the shutdown method from within command line:

```
sudo shutdown -h now
```The laptop does indeed fully power down. Just when I choose shutdown from the GUI it hangs. It seems to be a problem with just shutting down as I can reboot within in Ubuntu fine.

My laptops setup is a dual boot configuration, I have Windows 7 and Ubuntu 9.10 but I also have a D:/ drive which is the recovery drive for Vista when I had Vista home basic installed not sure if that helps anyone at all.

Not sure if this has been reported in 9.10 already, if so I apologise and hope someone can direct me to a fix.

Thanks for reading and any help given :)

**Just want to add: I never had any problems with shutting down in 9.04 the only problem I had was with waking my laptop up when Ubuntu was suspended or had been in hibernation, though from what I read this was a wide spread problem and has been fixed (For me anyway) in 9.10 just this pesky shut down issue!**

- James

---

### Post by benrb on 2009-10-30
I have the same problem with an HP desktop. Didn't have this problem with 9.04.

---

### Post by James2k on 2009-10-30
> **benrb said:**
> I have the same problem with an HP desktop. Didn't have this problem with 9.04.

Yeah it's strange from having no problems with 9.04. Does your screen also go blank or does it display any error message. I've read alot of "can't shutdown properly" threads that people encounter different stages where the shut down stops working.

---

### Post by James2k on 2009-10-30
Strange, I've just booted into recovery mode and selected "fix broken packages" and it's updated a few things, I've just shut down using the Ubuntu GUI and it shut down properly! Not sure if that was just a fluke but I'll keep checking on it.

**Edit: Seems it was a fluke, still hanging on a shutdown through the GUI from 20 mins ago**

---

### Post by gvor54 on 2009-10-30
same problem here

[http://ubuntuforums.org/showthread.php?t=1304987&highlight=gvor54](http://ubuntuforums.org/showthread.php?t=1304987&highlight=gvor54)

---

### Post by James2k on 2009-10-30
> **gvor54 said:**
> same problem here

[http://ubuntuforums.org/showthread.php?t=1304987&highlight=gvor54](http://ubuntuforums.org/showthread.php?t=1304987&highlight=gvor54)

Yeah it's really strange, I don't get any error message at all though, I think you could benefit by letting the developers know about your problem as some indication is given to why you can't shut down or reboot your computer, probably best to create a bug report in LaunchPad. I would to except I can't give any specific information about my problem and "It won't shut down" is no use to the developers.

---

### Post by James2k on 2009-10-31
Bump

---

### Post by benrb on 2009-10-31
> **James2k said:**
> Yeah it's strange from having no problems with 9.04. Does your screen also go blank or does it display any error message. I've read alot of "can't shutdown properly" threads that people encounter different stages where the shut down stops working.

Just goes blank.

---

### Post by otilesoj- on 2009-10-31
shutdown -h -P now
This should shuts down and power off.
I hope there is a fix for this so we dont have to do it manually but in the meantime this should work
Cheers and enjoy!

---

### Post by James2k on 2009-10-31
Yeah thanks for that. Myself I have been using:

```
sudo shutdown -h now
```

from terminal and it works fine, I have recently been able to shutdown my system through the GUI but it doesn't always work so there is some form of problem still, but anyway loving Ubuntu been spending a lot of time in Ubuntu than Windows recently. Probably because im not working and just messing around, but hey a great learning curve.

---

### Post by James2k on 2009-10-31
> **benrb said:**
> Just goes blank.

Similar problem to me then, I'll keep searching for an answer but if you use the command line method to shutdown your system you should be OK, temporary solution until the problem is corrected.

---

### Post by tkhalid on 2009-11-01
i am having the same shut down problems. it gives me a I/O error and it just hangs after that. o tried the "sudo shutdown -h now" and "sudo shutdown -h -P now" and it still hangs after giving the I/O error. i am a recent converter from vista to ubuntu so i have no idea if this is normal or something that shouldnt be happening. 

Any kind words or help would be appreciated. right now it feels like i made wrong choice to shift to ubuntu *fingers crossed*  i hope not !!!!

regards 

T.K

---

### Post by RuralHunter on 2009-11-02
I have the same problem since I upgraded from 9.04 to 9.10. I'm not able to reboot or poweroff remotely now. The server just closes all connections and hangs up. I have to push the power/reboot button on the machine. It's not acceptable for me!

Edit: btw, I installed 9.04 by wubi

---

### Post by bunta123 on 2009-11-02
On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :D

---

### Post by James2k on 2009-11-02
> **bunta123 said:**
> On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :D

Thanks for your reply. I will try this when I get home from College hopefully this helps other people having the same problem too.

---

### Post by Ray Carropa on 2009-11-02
> **bunta123 said:**
> On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :D

This works, I just had my first successful shutdown! Just wanted to add, paste rmmod snd-hda-intel at the top of /etc/init.d/halt file for new guys like me.

---

### Post by James2k on 2009-11-02
Thats excellent news, looks like a fix has been found for us!

Hopefully anyone that replied to this thread with a shutdown problem will hopefully find the fix and use it.

Thanks bunta123 for posting a fix!

---

### Post by trenn on 2009-11-02
**Re: Ubuntu 9.10 won't fully shut down**
 		On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :grin:


Hello,  I have been having the same problem since upgrading to v. 9.10.  If this modification works (and it seems to)  I would like to use it.  But..I'm not sure exactly where to insert the new line.  Ray Carropa said insert at the top of the file. That's fine and appreciated but not clear enough for 'really' new guys.  Pictures are great!  TIA  
Sincerely

---

### Post by James2k on 2009-11-02
> **trenn said:**
> **Re: Ubuntu 9.10 won't fully shut down**
         On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :grin:


Hello,  I have been having the same problem since upgrading to v. 9.10.  If this modification works (and it seems to)  I would like to use it.  But..I'm not sure exactly where to insert the new line.  Ray Carropa said insert at the top of the file. That's fine and appreciated but not clear enough for 'really' new guys.  Pictures are great!  TIA  
Sincerely

Well I've just tried out the suggested and it seems to work, my halt script had nothing in it so I simply added it in. Not sure if it's meant to but shut down seems to work so far!

---

### Post by trenn on 2009-11-02
PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt"
    halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:
Hi....This seems to be my halt file..It really doesn't mean that much to me..Seems to be different scenerios, which is why I'm not sure where to put the new line.  Thanks for any input....Sincerely

---

### Post by LENINMEN on 2009-11-02
Hey, I am also having a similar problem to the original poster. I have a compaq CQ50, and I can hear the hard drive shut down, but the power stays on, and the processor fan continues to run. The screen does shut off, so there isnt any error messages. 

I tried the above suggestion by adding that line, however it hasn't corrected the problem. If I see an answer somewhere, I will post it here

---

### Post by wazzle on 2009-11-02
Just added the line and works like a charm.  Thanks for the quick fix on this one guys. I think my 9.10 is working fine now. Here is a copy of my halt file with the addition for those who are asking where to insert the line. 


#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

[COLOR=Red]rmmod snd-hda-intel[/COLOR]
NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt"
    halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:

---

### Post by RuralHunter on 2009-11-02
> **bunta123 said:**
> On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown. :D
Great! It works for me. Thanks a lot buddy. but, what does this line actually do and why it can fix the issue?

---

### Post by CaKiwi on 2009-11-03
bunta123's fix worked for me too. I added the line to the end of the halt script

~CaKiwi

---

### Post by kilkenny on 2009-11-03
Hi guys

The 'rmmod' command in the '/etc/init.d/halt' file did not work for me.

But I found another solution. I changed the setting 'acpi=off' in the '/boot/grub/menu.lst' to 'acpi=force'.

I'm on an HP Compaq 6710b Notebook and I did an upgrade from 9.04 to 9.10, not a fresh install.

Hope that helps.
Adrian

---

### Post by SuperMetroid on 2009-11-03
What bunta123 posted allows my computer to shutdown.
But it's not a fix because the I/O errors still happen (more of a work-around).

---

### Post by BeStanly on 2009-11-03
Hi all!
this fixed my problem.this is my first aport to this site. i hope to do it well.
The same problem happen to me. The problem is (aparently) is wubi Because this:
I had the same problem when i used the iso image wubi.
I downloaded the .iso image from the official site and wubi 9.10 ([wubi-installer.org/]("http://wubi-installer.org/")). Then I used (in my case) daemon tools for the image only for putting it in the virtual device but i didnt installed. then i used wubi and it reconized the image from the device. next wubi did the instalation normally AND THAT IS IT!!
if you do it you will notice that after you reboot, the installation will be in a elegant grafic user interface. thanks!!! i hope that this fix your problem up.

ps: My native language is spanish.excuse me if i did grammar mistakes;).

---

### Post by trenn on 2009-11-03
Hi..  First, thanks to Wazzle for the picture.  The machine will shut down.:)  My problem was hanging at shutdown after a I/O error, and as SuperMetroid suggests, the error is still happening.  No good.  Where would I go to find out where the malfunction is?  Thanks to all.

---

### Post by janzen on 2009-11-03
Just forget, what I said here before. I had a new shutdown freeze.

---

### Post by neednewlaptop on 2009-11-03
Hello,

I am new to this forum and have been using ubuntu for about one year now. My laptop, an acer aspire 1681 wlmi, used to worked fine with 9.04. But an upgrade to 9.10 caused several problems including not shutting down completely. 

The last things I see are:
* Asking all remaining processes to terminate...
* Deconfiguring network interfaces...
* Deactivating swap...
* Will now halt

But it does not poweroff. Running shutdown -H or shutdown -P in terminal has the same effect as shut down from gui: no complete shutdown.

I wiped my disk and did a clean install, so the acpi=off to acpi=force in menu.lst solution is out since I am now using grub2.

The rmmod snd-hda-intel solution doesn't help either.

I seem to remember having as similar problem with 9.04, but then I switched off acpi and had no problem when just using apm. But services-admin is gone in 9.10 en BUM does not seem to handle upstart (other threads on that matter).

I really hope someone knows the answer.

---

### Post by jeffbarish on 2009-11-03
I agree with neednewlaptop.  The rmmod snd-hda-intel solution doesn't work for me either.

My system did power down when I first upgraded to Karmic.  Then it stopped.  Then it worked again for a short time.  Now it doesn't power down.  I'm not aware of any changes related to power-down behavior.

BTW, how do I turn off the Ubuntu logo during shutdown so that I can read the messages?

---

### Post by CaKiwi on 2009-11-03
I was too hasty with my last post. The first time shutting down after adding rmmod snd-hda-intel to the halt script worked, but it hasn't worked since.

---

### Post by neednewlaptop on 2009-11-03
I tried the acpi solution idea, but adjusted it to grub2. I edited the line GRUB_CMDLINE_LINUX="" in /etc/default/grub and then ran sudo /usr/sbin/update-grub to generate a new grub.cfg

I tried acpi=force, acpi=off, acpi=off no acpi, apm=on acpi=of and just apm=on. That had all kind of results, but still no complete shutdown.

Btw I can only see the messages I mentioned earlier when I push the power button for a few seconds, just not long enough for poweroff, otherwise I just see a blanc screen.

---

### Post by wazzle on 2009-11-04
I also spoke too soon.  My computer shut down the very first time after the line was added but hasn't shut down since. I still get the I/O errors too, then it just locks.

---

### Post by soma123 on 2009-11-04
Hi,
coment #19 in  [https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589")  seems to fix this problem.

Cheers!!

---

### Post by SuperMetroid on 2009-11-04
> **soma123 said:**
> Hi,
coment #19 in  [https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589")  seems to fix this problem.

Cheers!!

It works! I thank thee.
My computer shuts down instantly now.

---

### Post by neednewlaptop on 2009-11-04
I still does not work, no complete shutdown. I also tried apm=power-off in grub, it worked for the first time I shutdown the laptop, but the next time I had the same problem again.

---

### Post by marc66thomas on 2009-11-04
I'm new to this thread but also  *Began* my issue as a shutdown problem. I must have been impatient and halted the shut down poorly. I got on Screen dactavating swap.... wait... 136000139 buffer i/o errror on device loop 0 .... Wait ..... Logical block 4007946...

I've been trying to run "e2fs" to repair the disk I read that as a problem later in the Shut dowms must have bashed up the disk. Poor disk..

My system is a desktop with ubu over win 7  9.04 no prob. ubgrade 9.10 issues.  

Thanks All

---

### Post by CaKiwi on 2009-11-05
> **soma123 said:**
> Hi,
coment #19 in  [https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589")  seems to fix this problem.

Cheers!!
This worked for me too, thanks soma123

---

### Post by wazzle on 2009-11-05
Ok, this is the fix listed on bugs launchpad listed above. 

[COLOR=Red]Hi please try the following from an dist-upgraded Wubi Jaunty installation:[/COLOR]
 [COLOR=Red]edit /etc/rc6.[/COLOR][COLOR=Red]d/S40umountfs[/COLOR]
 [COLOR=Red]replace[/COLOR]
 [COLOR=Red]fstab-decode umount -f -r -d $WEAK_MTPTS[/COLOR]
 [COLOR=Red]with[/COLOR]
 [COLOR=Red]fstab-decode umount -r -d $WEAK_MTPTS[/COLOR]
 [COLOR=Red]and[/COLOR]
 [COLOR=Red]fstab-decode umount -f -v -r -d $WEAK_MTPTS[/COLOR]
 [COLOR=Red]with[/COLOR]
 [COLOR=Red]fstab-decode umount -v -r -d $WEAK_MTPTS[/COLOR]




I have a nano window open following typing your commands. But it is blank except for some menu options at the bottom. which appear to be shift commands for help etc I am a bit stuck and probably out of my depth. I don't see anywhere to edit any commands. I know there is something I am missing.

---

### Post by CaKiwi on 2009-11-05
Here's what I did. 

1) Opened a terminal window
2) Entered sudo gedit /etc/rc6.d/S40umountfs
3) Moved the cursor to the line
   fstab-decode umount -f -r -d $WEAK_MTPTS
4) Removed the -f from this line
5) Moved the cursor to the second line mentioned and also removed the -f
6) Saved the file
7) Rebooted

Hope this helps

---

### Post by geoffree on 2009-11-05
Me too!  The shutdown thing I mean.  How to change the code that is behind the GUI icon "shutdown"?  That would be interesting.

Geoffree

---

### Post by geoffree on 2009-11-05
How come I didn't see your post when I posted my post?  Had I not gone all they way through the list? Is your post an answer to mine? Not clear on the concept. Anyway, before I try it, does your code get activated when cliking on the "shutdown" button?
Or?

Geoffree

---

### Post by mark111 on 2009-11-05
Fix in post #41 worked great for me with an ASUS 1004HA.  Many thanks.

---

### Post by CaKiwi on 2009-11-05
> **geoffree said:**
> How come I didn't see your post when I posted my post?  Had I not gone all they way through the list? Is your post an answer to mine? Not clear on the concept. Anyway, before I try it, does your code get activated when cliking on the "shutdown" button?
Or?

Geoffree
Yes, the script that you edit is one of the things gets executed when you do a shutdown through the gui

---

### Post by neednewlaptop on 2009-11-06
Still no luck, it doesn't work for me. I noticed that during the shutdown proces I sometimes get the message:

init: sreadahead pre-stop process (1604) killed by TERM signal

Does this mean anything relevant to shut down?

---

### Post by wazzle on 2009-11-06
> **CaKiwi said:**
> Here's what I did. 

1) Opened a terminal window
2) Entered sudo gedit /etc/rc6.d/S40umountfs
3) Moved the cursor to the line
   fstab-decode umount -f -r -d $WEAK_MTPTS
4) Removed the -f from this line
5) Moved the cursor to the second line mentioned and also removed the -f
6) Saved the file
7) Rebooted

Hope this helps


Thanks for that post. It worked perfectly and all is well.

---

### Post by rforums on 2009-11-06
works like a charm.. :D
thanks..

---

### Post by geoffree on 2009-11-06
I tried your fix...taking out the -f flag.  But it did not change the shutdown problem.
Is this a machine-related fix?  I have an IBM ThinkCentre Desktop.  I also tried the inserting a line in /etc/init,d/halt "rmmod snd-hda-halt".  It didnt.  Has anyone an idea about this?  What about the clever folks who wrote the code?  


Geoffree

---

### Post by CaKiwi on 2009-11-07
> **geoffree said:**
> I tried your fix...taking out the -f flag.  But it did not change the shutdown problem.
Is this a machine-related fix?  I have an IBM ThinkCentre Desktop.  I also tried the inserting a line in /etc/init,d/halt "rmmod snd-hda-halt".  It didnt.  Has anyone an idea about this?  What about the clever folks who wrote the code?  


Geoffree
The fix in post #41 is for a shutdown problem that happens when a Jaunty system that was installed using Wubi is upgraded to Karmic. I don't think it is machine releated.

---

### Post by derrylynne on 2009-11-07
Thanks very much for that one. Item 41 did it for me:-)

---

### Post by mignacio79 on 2009-11-07
> **wazzle said:**
> Just added the line and works like a charm.  Thanks for the quick fix on this one guys. I think my 9.10 is working fine now. Here is a copy of my halt file with the addition for those who are asking where to insert the line. 


#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

[COLOR=Red]rmmod snd-hda-intel[/COLOR]
NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt"
    halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:

Thanks wazzle!! It works at last. Greetings from Patagonia Argentina.

---

### Post by neednewlaptop on 2009-11-08
My laptop has a button to switch off wlan. I usually push that button and then shutdown the laptop, which then doesn't shutdown completely. Now I noticed that when I don't push the wlan button the shutdown is complete. But I sometimes use it without connecting to wlan, so leaving that button on is not an option. Does anyone know how to prevent wlan from blocking shutdown?

---

### Post by hexwind on 2009-11-08
I have the very same problem too with 9.04 which i installed too days back. That command didn't work for me tho and I tried two other ones too which had the same results as well.

---

### Post by e0h1 on 2009-11-09
There are times when I try to restart(or maybe it was shut-down...I forget), that the screen freezes and shows a colorful mess with Webding letters across the top of the screen

I was going to try to get a picture of this, but when I tried restarting just a minute ago it worked.  Figures lol

---

### Post by SaintJules on 2009-11-09
Hi, I'm also experiencing some problems with the shutdown after upgrading to 9.10. Actually mine looks line a minor anomaly...but still: shutdown works normal as usual, the only thing is that the LAN's led on my desktop remains on and flashing. Suggestions?? 
Thanks

---

### Post by The Spy on 2009-11-10
I have a Apple Powerbook G4, and I have found that if I do not have my Broadcom b43 wireless drivers installed, that my system will shutdown/restart completely. Can anyone else confirm this with any other hardware?

---

### Post by neednewlaptop on 2009-11-10
My shutdown problems appeared to be related to my wlan too. I have an acer aspire 1681wlmi with the ipw2200 driver.
 
But I have wiped 9.10 and installed 9.04 again. I had enough of 9.10 trouble, 9.04 works perfectly.

---

### Post by e0h1 on 2009-11-12
So it happened again, and I took a picture

[IMG]http://i36.tinypic.com/2cfbc68.jpg[/IMG]


Anybody else get this?
[IMG]http://tinypic.com/r/2bti6v/4[/IMG]

---

### Post by James2k on 2009-11-13
> **e0h1 said:**
> So it happened again, and I took a picture

[IMG]http://i36.tinypic.com/2cfbc68.jpg[/IMG]


Anybody else get this?
[IMG]http://tinypic.com/r/2bti6v/4[/IMG]

I believe that screen appers when the video card resets into a new mode. It usually happens on a restart. I don't think there's any harm in it.

---

### Post by raghaviyengar on 2009-11-15
worked for me...thanks :)

---

### Post by e0h1 on 2009-11-15
> **James2k said:**
> I believe that screen appers when the video card resets into a new mode. It usually happens on a restart. I don't think there's any harm in it.

Why is the video card resetting into a new mode?

---

### Post by The Spy on 2009-11-24
This is was I get when I attempt to shutdown *with* wlan drivers installed.
Sorry for the poor quality.

---

### Post by ganeshmallyap on 2009-11-29
While shutting down my Karmic AMD64 desktop I too use to receive an error message saying "Deactivating swap..." and the system use to freeze.  Tried various solutions given in this forum but could not get over this.  Finally I did a Swapoff and then Swapon from gparted.  After this I never got this error.  Not sure whether this solution will work for others too.

---

### Post by Krakken on 2009-12-01
Hi everyone,
i'm new on this part of the net, hopefully things will get interesting and useful.

I do have the shutdown problem but it looks like my systems doesn't go in a loop. It freeze with the following writing on a black screen:

"Shutting down ALSA...
Asking all remaining process to terminate...
Deactivating swap..."

I use to get a freeze on a king of log in 
"DG login:_"
and after your fix
> 
[COLOR=Red]rmmod snd-hda-intel[/COLOR]
I'm getting this differnet problem.

I'm running a fresh Ubuntu 9.10 install on a eeepc 701 4G without any other issue.
The partitioning is without a swap to reduce i/o to the SD.

Hope this can help

---

### Post by Krakken on 2009-12-02
And more, if I use from the terminal

```
sudo shutdown -h now
```

the system doesn't shut down properly and freeze in the same "Deactivating swap..." line...

Does anyone still follow this thread and bug???

---

### Post by rizalbrandan on 2009-12-12
hello i have the same problem, but my problem solved with configure GRUB2 by editting /etc/default/grub[B] 

in the line [/B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

i add acpi=force

so the line is GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

then save

after that make update-grub

when i try shutdown my computer shutdown normally


[B]
[/B]

---

### Post by eckschi on 2009-12-29
Hi, 

none of the above solutions worked for my aspire 1600, turns out in my case it was the kernel which needed an update (from 2.6.31.16 to 2.6.32) 
see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479643](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479643)

hth 
 eckschi

---

### Post by dante6913 on 2010-01-07
> **eckschi said:**
> Hi, 

none of the above solutions worked for my aspire 1600, turns out in my case it was the kernel which needed an update (from 2.6.31.16 to 2.6.32) 
see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479643](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479643)

hth 
 eckschi


Thanks finally my shutdown is working

---

### Post by dante6913 on 2010-01-08
> **dante6913 said:**
> Thanks finally my shutdown is working

This works like charm, even crashes with firefox went a way and for the first time my Acer Aspire 1680 can suspend:D

---

### Post by hantechbl on 2010-01-08
Try sudo init 0

---

### Post by Chaddx on 2010-02-17
same problen, ubuntu just close the visual enviroment then just appears some kind of words, and pc never shut down, help please!!! :-?

---

### Post by confused_user on 2010-03-09
OK i have tried all of the above and none of it works.

This is what i see if i issue reboot form maintenance mode

init: rsyslog-kmsg main process (996) Killed by TERM signal
init: hal main process (1034) terminated with status 1
init: avahi-daemon main process (1042)n terminated with status 255
*stopping TiMidity++ Alsa midi emulation...
modemmanager: caught signal 15, shutting down...
init: disconnecting from system bus...
_

and then it just sits there with the flashing cursor until i hit the power off switch.

This is a deal breaker for me since i use a netbook.  i want to be able to close the lid and put it away and move on with me life.  Is that too much to ask?

At this point i would be happy to just hit the shutdown button and wait for a few minutes.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509) is not getting answered, not even assigned to anyone.  This bug gets about 104,000 hits on google so it's not a small bug.

I'm running 2.6.32-16-386 #24-Ubuntu SMP Sat Mar 6 15:33:03 UTC 2010 i686 GNU/Linux
 and have tried all of the stock kernels to no avail.

I will kiss the person who can solve this for me!

edit: i'm thinking that it may be something to do with hal not shutting down properly.

---

### Post by Welly Wu on 2010-03-22
I found a simple solution that works for my Toshiba NB205-N310/BN netbook running Ubuntu 9.10 Karmic Koala: uninstall SELinux. I used the Synaptic Package Manager to uninstall SELinux and re-installed AppArmor. Then, I tested both the reboot and shutdown on my PC and it worked for me.

---

### Post by itagomo on 2010-03-22
> **Welly Wu said:**
> I found a simple solution that works for my Toshiba NB205-N310/BN netbook running Ubuntu 9.10 Karmic Koala: uninstall SELinux. I used the Synaptic Package Manager to uninstall SELinux and re-installed AppArmor. Then, I tested both the reboot and shutdown on my PC and it worked for me.

I hope this is the solution that will work for my 1-week old Karmic Koala. I can reboot, but hangs when shutdown.

---

### Post by QuaGon on 2010-03-23
i have the same problem.. will reboot fine but when i try to shutdown, the cpu stops but the other fan and general moniter and pc power stays on. i have to do the last step holding the power button for 5-6 secs..

---

### Post by warsev on 2010-03-28
I now have this exact problem with Karmic since the kernel update from 2.6.31-20 to 2.6.31-21 about three days ago. When shutting down from the GUI my Dell Inspiron 9100 laptop goes through the motions for a while, then just hangs with the screen backlight turned on but blank (black), fans running, everything else dead. I have to hold down the power button for about ten seconds to finally shut the thing off.

Hope somebody finds and squashes this bug.

---

### Post by slackfish on 2010-03-30
> **rizalbrandan said:**
> hello i have the same problem, but my problem solved with configure GRUB2 by editting /etc/default/grub[B] 

in the line [/B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

i add acpi=force

so the line is GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

then save

after that make update-grub

when i try shutdown my computer shutdown normally




This worked for me, running on a HP Pavilion 6635 (Celeron).  Discovered it after installing and unsuccessfully running an older kernel from 9.04.  However I noticed an error at boot that read something like 'NO DMI BIOS DATE try adding acpi=force to kernel parameters'.

---

### Post by RichardSM on 2010-04-15
Hello I have a shutdown problem?

My computer use to run 8.14 LTS I ordered a 9.10 CD from the site in the UK and recd. last week I installed it. And made it a full partition as it was before now it won't shutdown I think it turns off the HD the screen goes black after few min. but the fan stays on and the computer light stays on as well along with the mouse too. It’s an AMD 1400 Thunderbird processor 512Kb memory home built machine, the mother board is made by MSI. IT ran very well when I ran it hard wired it work just fine but I moved it to a location where I tried to use it wirelessly using 8.14 could not get to work that way. So that’s why I ordered 9.10 hoping it would work but now it won't shutdown properly. Any help would greatly be appreciated. Thank you

---

### Post by RichardSM on 2010-04-15
Re: 9.10 shut down problem 

--------------------------------------------------------------------------------

Ok Thanks

Can you point to a site for the latest kernel. I went to 2 sites both are not working. 

Update 4-14-10
All right I downloaded a new kernel. (Kernel Linux 2.6.31.14 generic) still no difference.

--------------------------------------------------------------------------------
Last edited by RichardSM; 17 Hours Ago at 12:36 PM..

----------------------------------------------------------------------------------------------------------------------------
Is this a problem that just can't be fixed! I have tried all most all the fix&#8217;s none work so what reason for this there s got to a fix somebody knows the how or what that can fix this problem. Thank you to all who have worked on this problem..

Update April 17 2010 06:56 Hours

(Solved)
Hello
I found the right HACK or FIX for my problem after trying a few of the posted items see below, after each hack I tryed shutdown using the GUI No Help on any of them except for the last HACK or Fix if you will.

1: Open terminal  sudo gedit /etc/init.d/halt rmmod snd-hda-intel 
2: Terminal sudo gedit /etc/default/grub in this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" I added acpi=force
   so the line should look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" then save then do in terminal      update-grub
3: Terminal  sudo gedit /etc/rc6.d/S40umountfs Moved the cursor to the line fstab-decode umount -f -r -d $WEAK_MTPTS and remove the -f form this line Now move the cursor to the second line and remove the -f from this line as well then SAVE the file and reboot.   One last thing I left all these changes in affect 

4: Terminal  sudo gedit /etc/default/grub I changed the line from GRUB_CMDLINE_LINUX="" to this GRUB_CMDLINE_LINUX="reboot=b" saved it and rebooted this one did the trick for me.

---

### Post by isbiyanto on 2010-04-15
sometimes i use Gshutdown from my GUI.
install Gshutdown from Ubuntu Software Center

---

### Post by James2k on 2010-04-16
I found another solution to this issue is add acpi=force on:

> GRUB_CMDLINE_LINUX_DEFAULT

In the grub.cfg. Edit /etc/default/grub (Make sure your root when you edit this file) and run update-grub after you make the change. 

Shutdowns should be fine after that. Though in recent versions of Ubuntu, shut down problems are becoming less and less.

---

### Post by Bangalow on 2010-04-18
Hi 
I tried to shut down with (sudo shutdown -h now)  but no good. It just hangs on the blank screen. I shut down by hard shutdown (pushing the power button) It is ok when you boot up again.
All was fine with 9.0.4

---

### Post by kcredden on 2010-05-11
Hi folks: I started having this problem, /after the last big update/ just before 10.04 was released. Never had this problem until now. Also I will note that I just did a complete wipe/reinstall (I was playing around and screwed it up) gave it the full 300+ meg update, and yep. Same problem. So there's something there it seems. 

My system is Ubuntu 9.10 w/both Gnome, AND Xfce 4.x It won't shut down on either GUI.

Hope that helps. Thanks for the command line shutdown. I've made a button in the panel that issues this command instead of using the standard button.

- Kc

---

### Post by hfelton on 2010-05-18
bump - id been doing the nominal updates to edubuntu-9.10 and something broke the shutdown in the gui within the psat couple of days...  i get the black terminal screen saying three things (last of which is system-is-halting), but the power does not turn off automatically like it -used-to- for the past 6 mos...

other than normal updates, i do not think i did anything (like install sw or change settings) - just the usual email/web-surf stuff...

i hit the power-button (4 secs) and it turns off fine and reboots with no error messages...  also, if i interrupt grub-auto-boot (i think i have like 4 different kernels and their recovery-items, so like 8 choices) by hitting the -c- character to get a command prompt...  if i then type the simple command -halt-, then the power goes off as expected...

unfortunately i do not remember what got updated in the past week or so when i did the update-manager, so i dont know where to look for this bug...

any clues/ideas/common-symptoms ?  thx, h.

---

### Post by timonner on 2010-05-26
Hello to all
I have the same problem. My system configuration is: Ubuntu 9.10, kernel 2.6.31-21-generic.
Few days ago I have updated my OS and I forget what was updated by Update Manager. But one thing I remember - the problem borned after update the system.
Hope this bug will be fixed.


The problem was solved. I updated kernel to 2.6.32-22 and all working now!! 

=]

---

### Post by kansasnoob on 2010-06-19
I've been real busy the past couple of weeks but recently reverted to using Karmic as my "stable" OS whilst I sort out a couple of unrelated minor Lucid bugs. I multi-boot anyway so it's simply a matter of booting into the most stable OS of the moment :)

But upon doing so I encountered this "shutdown" bug. Since my time was limited I simply created a custom launcher in the panel to "shutdown -h now" until this AM when I began trying different work-arounds. Sadly none worked :(

I finally began parsing through updates and discovered that if I downgraded "linux-libc-dev" and booted the old "2.6.31-14" kernel the problem disappeared. Of course I didn't want to use that old kernel so I grabbed the mainline kernel here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.13-karmic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.13-karmic/) 

Instructions here:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

Anyway, that did it for me so I thought I'd add this info as one more possible solution for others who might face this problem. FYI I'm using the i386 build w/Intel Atom 230 and i945 graphics, and this is a true install, **not Wubi**.

---

