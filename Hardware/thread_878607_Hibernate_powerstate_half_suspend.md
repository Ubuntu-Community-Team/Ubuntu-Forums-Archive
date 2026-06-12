---
title: "Hibernate powerstate half suspend?"
date: 2008-08-03
forum: Hardware
---

### Post by misho1721 on 2008-08-03
I've searched around and have come up with this:

I have a Toshiba A205-S5825, everything works great except for one thing.

Sometimes when my computer wakes up from hibernate it will not power on the fan and (I assume) would overheat, It can read the temperatures but cannot kick the fan on(works from reboot or cold boot).

I know that this is a known issue for some computers, however I have noticed one thing, When hibernating from Ubuntu the system does not enter the same state as when it hibernates from vista (I'm not switching while one OS is hibernated) When hibernated from vista the laptop will not turn on if opened only when the power button is pressed, After being sent into hibernation by Ubuntu, opening the lid powers on the system.

My question is how can I have Ubuntu send the same ACPI event as when shutdown is selected. It seems that if after saving the RAM to disc and reading itself for hibernation if I could just have it send the same signal to the BIOS as a shutdown it would solve the fan problem as it always works from a reboot or a cold boot.

Thanks, Sorry for the novel

Toshiba Satellite A205-S5825 Ubuntu 8.04.1

---

### Post by grungedoobie on 2008-08-10
** Begin Edited Note **
I have found that doing this does keep the computer cool under normal operation.  However, running programs requiring larger amounts of processing generates more heat.  Therefore, the following is not advisable for those who wish to use their computer for gaming.  I will try to find a way to monitor the CPU useage so that the fan script can automatically adjust itself to what you are doing.  I'm thinking something like on 3 of 5 mins if CPU is less than 33%, then on 4 of 5 mins if CPU is 33% to 66%, then on 5 of 5 mins if CPU is above 66%.  This may take me some time as I am still learning, but I will give it a go as I want my laptop to be self monitoring so that I don't have to guess.
** End Edited Note **

Hello, I am new to these forums, and only have a little over two years and six successfull installs worth use with linux.  ( The prior mentioned installs do not include the multiple installs used while playing with platforms on different machines. )  But this is another matter.

I recently acquired an old Toshiba Tecra 8000 in payment for services rendered on a Toshiba Satellite.  The Tecra was in original condition including (I made all upgrades): Pentium II 366MHz, NeoMagic on-board video with 2.5Mb aperture, 64Mb Ram (upgraded to 256), 8GB HDD (upgraded to 80GB), 4x Cd-Rom (upgraded to 20x Cd-Rom/4x Cd-RW/2x DVD), 14.1" TFT LCD Display, the only source of network connectivity installed is an on-board Chinese made microsoft modem (which seems to hate linux code) and of course 1 dead battery (upgraded to highest available capacity).  I've pulled these specs from my memory, so they may not be 100% but they are as accurate I can make them without a cheat sheet in front of me.  I also purchased an "Ethernet through USB" adapter for my one USB port (It was cheap and I like to play - came in very handy for primary installation though), and a LinkSys Wireless G PCMCIA network card.

I tried installing DSL, Puppy, Suse and Slax flavors, but they all had major problems with the hardware requiring some serious hacking which I am not very good at.  XUbuntu was the closest to fitting the bill by being able access and run the majority of the hardware available.  The "Ethernet to USB" adapter was detected and connected without having to tweak using the "Live-CD" (by the way, I used the XUbuntu Hardy Heron x86 Alternate ISO for the Live-CD).

Ok, that being said, I also noticed a heat problem.  The laptop would become quite uncomfortably hot before the fan turned on, and on occasion it would become so hot that the system would become very - very slow, so I would shut down and let it cool off.  Something else that I noticed at start-up a line would come up saying (in short) "no ACPI,ACPI=Force".  From what I gather, ACPI is used for monitoring hardware performance and condition.  Oh, I also noticed that when running on batteries, the fan rarely if ever turned on, allowing the computer to become that much hotter.

Now for the good stuff, as this is how I fixed it.  There is a fellow who reverse engineered a Toshiba and learned the code to send commands directly to the hardware telling it what to do.  This package is called "toshset".  I found it after trying some other hardware negotiation packages that could do just about everything but tell me the temperature of the chip or anything else about other hardware outside of CPU Usage, Memory Usage and cache size.  I checked to make sure toshset work by invoking the command: "sudo toshset -q".  This gave me the state of the hardware but still no temperature readings.  I used this command to turn on the fan: "sudo toshset -fan on".  Sure enough, the fan turned on.  I double checked to make sure the command was not a simple toggle by repeating the line and it did not toggle the fan, the fan stayed on.  I then invoked "sudo toshset -fan off" and sure enough, the fan turned off.  The next thing was to write a simple script to turn the fan on and off at intervals, then to find a way to repeat the script in a stable manner so that the laptop is never more that 5 minutes away from relief.  The following is what I did, and it worked for me.

From the shell prompt:

sudo mkdir /usr/share/toshfan

--This makes a directory to put the script

sudo gedit /usr/share/toshfan/fancycle

--This opened "Gedit" (you may need to get gedit from 
--repository or use the text editor of your choosing)
--and created a text file called "fancycle".

--In "Gedit" I wrote:

## ** WARNING THIS IS DANGEROUS!!! **
## OMIT LINES 2 AND 3 IF YOU ARE GAMING
## IT IS BEST TO LEAVE FAN ON ALL THE TIME
## THEN TO HAVE A CRISPY FRIED CHIP
sudo toshset -fan on
sleep 3m
sudo toshset -fan off

--This tells the fan to turn on, wait three minutes then
--turn the fan off.
--I then saved and closed "Gedit" and went back to shell
--I then entered:

sudo chmod 755 /usr/share/toshfan/fancycle

--This makes executable the "fancycle" text script.
--I then entered:

sudo crontab -e

--This put me in a simple script editor (very basic).
--I made this entry:

*/5 * * * * //usr/share/toshfan/fancycle

--I then pressed "Ctrl-o" (that's a letter not a number)
--I then pressed enter
--This saved the new entry to cron
--I then pressed "Ctrl-x" to leave the editor.
--The entry into cron invokes the "fancycle" script every
--five minutes as long as the laptop is turned on no matter
--who is logged in.
--The following command will verify that the entry was accepted:

sudo crontab -l

--This tells cron to list all root entries.
--And of course the listing should contain the entry made.
--That's all, and it works for me.

I don't mind sacrificing a little battery time to make sure the laptop doesn't catch fire.

WARNING:  Always check your commands before committing.  If the command doesn't work in shell, chances are that they don't work at all.

--Now THAT was a novel, lol--  The Grunge

---

### Post by grungedoobie on 2008-08-10
An added tidbit for those who are unaware.  Electronics generate heat when in use.  (Especially electronics that require an external cooling source.)  The hotter the electronics get the more electricity is needed to keep running creating a vicious cycle of heating up then drawing more electricity until meltdown.  The cooler you can keep your electronics the more efficiently it will run and the longer it will last.

The Grunge

More info:  There should be an option somewhere in either the power management or the screensaver advanced options that tells linux what to do when the lid is closed.  Granted, I am running Xubuntu on mine but the option for shutdown when lid is closed is there.

Hope this helps  8-)

---

### Post by misho1721 on 2008-08-16
Thanks for the info though it seems to not apply toshset said it's modules were not installed and "fan" says it is not supported.

Well I finally made some progress on this. having 

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

in my /etc/default/acpi-support

either lets the fan turn on and off normally (like a cold/reboot) or makes the fan stay on constantly (which I'd much rather have)

Are there and other values for this line (assuming shutdown is valid, it had an effect though) Or a document on this file?

It still wakes from hibernate if opened, I don't think it should but all I have is Google and poking around in files :)

---

### Post by grungedoobie on 2008-08-17
If the "sudo toshset -q" command isn't giving the proper info on your system bios, you could check with the synaptic package manager to see if "toshset" and "toshutils" are installed.

My laptop automatically installed the "toshset" package, but I had to get the "toshutils" for the thing to work properly.  Something about "toshutils" being community maintained makes it not a part of the canonical.

I believe that it is a medibuntu package if that helps any.

If you don't have the medibuntu repository, their website is:

[http://medibuntu.org](http://medibuntu.org)

They have the how to and what to do to install their repositories.

Please be careful when playing the the fan.  And, it's always a good idea to be mindful of a laptops temperature whether or not the fan settings were modified.

I've set mine to just run all of the time so that I won't worry about it so much.  By doing that, I've only lost about 10 mins of battery time which is no biggie to me.

Ugh, one more thing, I do have some feelers out there to try to gain some insight on how to use a simple script program that monitors cpu usage and engages the fan by that means.  Ok, I'm done now, I promise.

Oh, and one more think......   lol  .....have fun  8-)

---

