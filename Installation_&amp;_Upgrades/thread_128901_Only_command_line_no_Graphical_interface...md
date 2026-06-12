---
title: "Only command line no Graphical interface.."
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by landlord on 2006-02-12
I installed 5.1 Ubuntu with some amount of pain (burning alternative cd's at lower speed, changing Cd player, etc..).

Now when the bloody thing got on to the the machine and unpacked successfully I get a black screen and a blinking cursor.

I can get to command line with ctrl+alt F1 but that is it. no bloody graphical interface.

Command startx is not working. it does the same thing as before. reboot not working, i get to the blinking cursor again. Damn blinking horizontal line. 

Here is what I was thinking about. Not sinkin´ as in Berlitz commercial but thinking as What the hell are you thinking about - a sign on some hot blonde´s T-shirt, thinking.

This macchine that I am trying to install Ubuntu on is quite old, I had problems with cd rom;i tried to install debian and debian got really confused when we came to graphics configuration, so I am thinking that maybe ubuntu messed up graphic card configuration.

So what I want to do first is to see what hardware is on my computer?
What command to use, which are the important information?

Then I would have to install additional drivers for this old hardware, again how do I do that or better where to find the proper drivers?

And last, but not the least I am in search for patience which is clearly far away  from me regarding all the bloody problems I am having with this bloody box of crap and forgoten nightmares.

\\:D/ 

Please help, fast.

>>Regards,
LL.

---

### Post by engla on 2006-02-12
There has been an unconfortable mass of people coming here with this problem recently [what I've seen]. I don't know the cause, but there are some things you can try.

I. Make sure everything is installed. Log in to the text console and try 'sudo apt-get install ubuntu-desktop' It should tell you that nothing needs to be installed, but install anything it tells you if it's needed.

II. Try reconfiguring your X server, as it's not starting. Running 'sudo dpkg-reconfigure xserver-xorg' should help you set it up properly, again in the text console.

---

### Post by landlord on 2006-02-12
Bloody box of nothing but infected bird crap.

I noticed that I have two video cards in slots, one of them ati all in wonder. i took ati out and after the start i got the blinking friend, but just for a moment, just after that i got an error of x terminal and ofcourse reconfigure after that helped.

first problem solved, now my father can browse the internet, so that i can peacfully install my freeradius server.

thank you my friend,
LL.

---

### Post by LoloMc² on 2006-02-12
Hello everyone, this is my first post on this forum ;)
And it is mainly to let you know that engla gave me the solution for the problem I ha ! 

Last morning I have installed Ubuntu 5.1 and everything was working well. (No hardware problem, everything was ok)

Unfortunately, this afternoon I have rebooted because I have tested the "Ctrl+Alt+F1" key ! 
Just after this reboot, my monitor told me "frequency out of range", bla bla bla. I were not able to do anything as I'm really a neeb with Linux (But I'm learning !!!)

I have spent several minutes (hours ???) googleling with my OTHER computer and find in the archive of that forum, a message, Like engla said, 'sudo dpkg-reconfigure xserver-xorg' should help you set it up properly, again in the text console.

And it works ! \\:D/ 

As on the 5.04 I had the "fail to ignitialize hall" bug at startup (I weren't able to do anything as well) maybe I can make a suggestion to the devellopers :
As it seems there is a lot of the problems who comes when reboot/startup, please include a "safe hardware mode" to be able to go to the GUI, to be able to go to the Internet to find what's happen and to try to reconfigure something... instead of formatting and reinstall. I did it 3 times this night

---

