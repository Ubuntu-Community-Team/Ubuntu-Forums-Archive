---
title: "Problem in sound on Presario CQ61"
date: 2009-07-07
forum: Hardware
---

### Post by -ICEBOX- on 2009-07-07
Hi,
 
I hope there's anyone can help me regarding on my HP laptop Presario CQ61. I'm using ubuntu 9.04 my problem is there's a speaker icon but there's no sound even I adjust the volume in 100%. Anyone can help me.. I'm also newly user of ubuntu and I want to learn I hope there's someone can guide me or give me the command in terminal to update my sound driver.. Thank you in advance and I really appreciate it if you can help me with this matter.
 
Best Regards

---

### Post by drbongo on 2009-08-01
ICEBOX - I had exactly the same problem! But I have just fixed it after several hours of pulling my hair out. I had tried everything I could think of, as well as lots of solutions other people had suggested, including installing the latest version if Alsa from source etc. Nothing worked, until I found these four lines on another forum. Simply paste them at the end of /etc/modules.d/alsa-base.conf and save it.


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo

---

### Post by pauljdunn on 2009-08-14
I have a similar problem, I have just got a Compaq Presario CQ61-135TU purchased specifically to run Ubuntu Linux or similar I can load Ubuntu but no joy getting the sound card or wireless internet working or (Web cam or Data card these are not so important)can anyone help me please **get the right drivers to get the sound card or wireless internet working?**

---

### Post by pauljdunn on 2009-08-14
Compaq Presario CQ61-135TU has the same issue with sound NOTHING THERE and internet does not recognize the wireless card :(

---

### Post by Joppe4899 on 2009-08-19
My wireless card works after I used this command. 

sudo apt-get install linux-backports-modules-jaunty

Works like a charm now

---

### Post by falkTX on 2009-09-03
> **drbongo said:**
> ICEBOX - I had exactly the same problem! But I have just fixed it after several hours of pulling my hair out. I had tried everything I could think of, as well as lots of solutions other people had suggested, including installing the latest version if Alsa from source etc. Nothing worked, until I found these four lines on another forum. Simply paste them at the end of /etc/modules.d/alsa-base.conf and save it.


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo

Many thanks!
Worked perfectly for me!

---

### Post by fotonic on 2009-09-04
> **drbongo said:**
> ICEBOX - I had exactly the same problem! But I have just fixed it after several hours of pulling my hair out. I had tried everything I could think of, as well as lots of solutions other people had suggested, including installing the latest version if Alsa from source etc. Nothing worked, until I found these four lines on another forum. Simply paste them at the end of /etc/modules.d/alsa-base.conf and save it.


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo


Many thanks Drbongo,
I had this problem: I got sound only through the headphones, but not through the speakers.
Don't know if this problem is realted to the installation of thenvidia  beta driver version 185.19 for my videocard Nvidia Geforce g103 m.
After installing that driver I noticed that sound worked only through the headphones.
Then I followed your instructions and added the four lines to "/etc/modprobe.d/alsa-base.conf", without success.
Then I followed this link [http://monespaceperso.org/blog-en/20...tu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")
and upgraded my alsa version, still without success.
I pulled many times my hair out and wanted to give up.
Then I followed yuor instructions a second time, and ....
incredible...
it works!!!

Audio now comes out through the speakers too!
Now I'm trying to configure dual-head with rotation of the external screen. Any suggestions?

fotonic

---

### Post by farroos on 2009-09-05
> **drbongo said:**
> ICEBOX - I had exactly the same problem! But I have just fixed it after several hours of pulling my hair out. I had tried everything I could think of, as well as lots of solutions other people had suggested, including installing the latest version if Alsa from source etc. Nothing worked, until I found these four lines on another forum. Simply paste them at the end of /etc/modules.d/alsa-base.conf and save it.


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo


VERY IMPORTANT!!!

There is a typo in this solution.

```
/etc/[COLOR="DarkRed"]modules.d[/COLOR]/alsa-base.conf
```

Thats wrong.
The correct place is

```
/etc/[COLOR="DarkRed"]modprobe.d[/COLOR]/alsa-base.conf
```

So basically upgrading to the latest alsa and adding the above four lines to the correct file will make the speakers work.

I've had a few rough hours until I found the typo, but many thanks to drbongo for helping us Linux newbies with our problems.

---

### Post by abusamra on 2009-10-07
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

what that mean and why it comes when i tried to save the file after update it

---

### Post by falkTX on 2009-10-08
> **abusamra said:**
> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

what that mean and why it comes when i tried to save the file after update it

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

replace gedit with kate if using Kubuntu

---

### Post by abusamra on 2009-10-08
> **falkTX said:**
> ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```replace gedit with kate if using Kubuntu

thanks a lot, i did this exactly. but it dosent work.   i have compaq CQ61-280EJ its new 
also i tried the command that mentioned above for fixing the wireless but it doesnt work also


hope that anyone help, because i like ubuntu and i dont want to get back to vista

---

### Post by falkTX on 2009-10-08
Have you tried to un-mute all channels from the volume mixer settings?

I usually have a problem (on a fresh install), because some "Speaker" setting is muted and volume all down.

You should try enable all the possible channels from the mixer options and set them all to MAX! (just to see if that works...)

(Worked for me)

---

### Post by santes_dad on 2009-10-09
You need to using a more recent version of Alsa, for your sound to work. Release 1.18 is the default in Ubuntu 9.04, it needs to be upgraded to Release 1.20 > or 1.21.

I just bought a CQ61 and upgraded to 1.20, plus adding those 4 lines into the aforementioned *.conf file. The sound is restored.

The thread to upgrade Alsa is as follows:

[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

Good luck!

---

### Post by falkTX on 2009-10-09
If you don't mind waiting a few days, the next Ubuntu version, Karmic (will be released at 29 this month), will fix this problems.

Maybe will still be needed to edit that file, but rather than that it all works fine

---

### Post by Nastro on 2009-11-12
Great. It works!! :D
Thank you very much!

//Nastro

---

### Post by voodoox on 2009-11-13
i make this configuration 


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo[/QUOTE]

---

### Post by pauts on 2010-01-21
hello

that works fine for the sound. but i have the same problem with the microphone.
the jack for the micro works, but not the built-in micro.

any help?

> **voodoox said:**
> i make this configuration 


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo[/QUOTE]

---

### Post by Ergorafail on 2010-03-12
> **abusamra said:**
> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

what that mean and why it comes when i tried to save the file after update it

Hi !
i have the same problem with abusamra,i have ubuntu 9.10 and i try to edit text with kate but i fail again

i need your help pleaseeee:(

(soory for my english i am from greece,thank's)

---

### Post by Ergorafail on 2010-03-13
omg...finally i did it,thanks for your information...

i open terminaland, i wrote:

*sudo gedit /etc/modprobe.d/alsa-base.conf*

and then i add in the end of alsa-base.conf this:

[I]options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1[/I]

i restart my pc,
**and yessssss i have sound...ouf** :D 

thanks a lot :)

---

### Post by snazzybottoms on 2010-03-22
thank you, thank you, thank you.
After literally an entire day wasted trying to get sound your solution did it. Was up and running w/ sound in like 2 min. thank you again.

---

### Post by eyeonus on 2010-04-24
I have this problem on Karmic, and the "fix" didn't work for me, either. Any suggestions?

---

### Post by lidex on 2010-04-24
> **eyeonus said:**
> I have this problem on Karmic, and the "fix" didn't work for me, either. Any suggestions?
Go here and work through the generic audio bugs in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Make sure to install the alsa-backports as detailed there.

Still no sound? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by eyeonus on 2010-04-29
It's fixed now. The link helped. Thanks.

---

