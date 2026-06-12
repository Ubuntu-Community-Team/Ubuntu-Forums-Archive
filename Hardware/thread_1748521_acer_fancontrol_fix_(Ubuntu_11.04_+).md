---
title: "acer_fancontrol fix (Ubuntu 11.04 +)"
date: 2011-05-03
forum: Hardware
---

### Post by dushmi94 on 2011-05-03
This is my first post on this forum :).

After studying some time I managed to fix the acer_fancontrol script. Now it works with Ubuntu 11.04.

It was tested on an Acer Aspire 5315 with 2 GB of RAM. This script should fix the problems with the overheating of the CPU.

You have attached the modified version of acer_fancontrol.

Here is the readme: 

1) Download the script

2) Change the directory

```
cd Downloads
```

3) Unpack the script

```
tar xvfz acer_fancontrol.tar.gz
```

4) Change the directory

```
cd acer_fancontrol
```

5) Pick the memory size which matches your memory size(it doesn't matter if the model isn't the same).

```
gedit acer_fancontrol
```

You can use other text editors too. 

The options are:

- 512 MB : delete the # from the beginning of the 77th line
- 1 GB : delete the # from the beginning of the 79th line
- 2 GB : delete the # from the beginning of the 81st line

6) Install the script

```
sudo cp acer_fancontrol /usr/bin
sudo cp mempat /usr/bin
```

7) Make it run automatically

```
sudo gedit /etc/rc.local
```

Insert "acer_fancontrol" before the final "exit 0" (without quotes).

I mention that I don't own this script. I've just edited it a little.

---

### Post by thelunga on 2011-05-24
Testing the solution.

thanks

---

### Post by KidneyBean on 2011-06-01
Hey, I'm a little confused. After downloading the script and then attempting to install via the terminal, I'm told "no such file or directory". A little help?

---

### Post by KidneyBean on 2011-06-01
I'm bumping this thread. No why? In the middle of attempting to post my first bump/reply, my Acer 5315 shut down on me. The stupid thing is as hot as an oven- the fan simply isn't kicking on (as usual). 

Now I asked nicely for a reply yet nobody wanted to help. I posted an entire thread about this issue and yet nobody could answer me. 

Right here in this thread the solution to my Acer shut down awaits- but yet nobody can help me out by explaining just why when I type into the terminal the install commands as listed above, that I'm told there is no such file or directory. I unpacked the download. I followed the instructions. PLEASE, what am I doing wrong???

My system is about to shut down again so I'll leave it at this.

---

### Post by Larkspur on 2011-06-01
> **dushmi94 said:**
> This is my first post on this forum :).

After studying some time I managed to fix the acer_fancontrol script. Now it works with Ubuntu 11.04.

It was tested on an Acer Aspire 5315 with 2 GB of RAM. This script should fix the problems with the overheating of the CPU.

Thanks for this!  I thought I'd have to stick with 10.04 on my Acer.

For the record, the script works on an Acer Aspire 5315 with 512MB RAM.

---

### Post by clskinny on 2011-06-08
I am super new to Ubuntu.

Where do I define the memory size?

When I use vim acer_fanctonrol it opens up a new terminal that appears to be some sort of text editor am I supposed to paste in the scripts from the fan control file or should this open the fancontrol file from that download?


Sorry if a lot of these questions are super newbish but I can't even experiment with the OS until I can get the laptop to stay on for more then 15 minutes.

Any info on modifying scripts or anything along those lines would be helpful. Fortunately it isn't my only computer so time isn't that big of an issue.

---

### Post by Dayve on 2011-06-12
I too have the same problem.
After I install acer_fancontrol the fan seems to work but when i do a reboot the screen gets stuck on 3rd gear without me being able to log on backtrack 5

---

### Post by Schteph on 2011-06-14
Hi,

Does anyone know the value to use with 4gb of RAM?

Cheers

---

### Post by dushmi94 on 2011-07-28
Sorry guys for this late answer... I've had some problems and I haven't been able to help you.

So, I've uploaded the archive again( there were some little mistakes) and I've edited the readme so that everyone can understand it now :). If you'll have more questions, please post them here.

@Schteph: Try with the 2 GB code.

---

### Post by antalkrisz on 2011-08-05
What if I have one and a half (1.5) GB RAM?

Upgrading the BIOS from v.1.19 to v.1.43 has solved the fan control problem :D.

---

### Post by ChronoMTB on 2011-08-16
Wow, man, it looks like I'm now able to use that Ubuntu 11.04 properly. Tried to solve the problem with acerhdf, though it did not work out for me. Upgraded BIOS + the script you edited seem to work perfectly on my Acer 1810tz. Thanks a lot. Still going to check out if everything really is ok now, but so far so good. Even the CPU sensors somehow got working now.

---

### Post by Larkspur on 2011-10-01
Does anyone know if this script works with 11.10?

---

### Post by basilsquire on 2011-10-23
This has worked for me on 11.10 with 1Gb RAM. Thanks alot, I was about to go insane with it dying all the time.

I got the message that there was "no such file or directory" too but I just ignored it and carried on and now the fan is running :o

---

### Post by osmoTR on 2011-10-29
lastest bios update solves fan issue script not required

---

### Post by rickNS on 2012-01-26
THANKS Dushmi94,

 This is the best how to on this subject, and I think I've seen them all.

 I'm actually using Mint 9 on Acer 5315, 32 bit with upgrade to 2 GB ram.

 My fan would come on maybe once in 15 or so start-ups. I didn't want to do the bios update for fear of dead computer, and thought if others got this to work, so will I.

 This is a tough one for newbies like myself, as it is hard to "play" with the computer when it is constantly overheating.

 If I may, and maybe you can add this to your post, as one user asked how do you select your memory configuration, you remove the "#" from those lines that apply to you when editing the acer_fancontrol file. Also I think it is necessary to have lm-sensors installed.

 I also installed screenlets to watch the cpu temp. it's now maintaining about 38 C

 VERY HAPPY Thanks again,

 Rick

---

### Post by deadfraggle on 2012-01-27
I installed the script, lm-sensors and screenlets on the Acer Aspire 5315-2822 laptop I'm working on with Ubuntu 11.10.  The reported temperature was never steady and showed 3% when the unit was obviously getting warm to the touch, and would report 99% at times when internet browsing or using the cd.  The fan never came on, and the laptop finally overheated and powered down.

Ubuntu was installed on an upgrade drive, and the original hard drive with Vista is untouched.  I was thinking of re-installing the old hard drive and using the included Acer software to update the bios.  Good or bad idea?

---

### Post by rickNS on 2012-01-28
Deadfraggle,

 Updating BIOS is not easier nor faster than this fix, and comes with the risk of killing your computer.

 This the best way to fix the fan issue, and this is the best set of instructions to do so.

 Read it over a couple of times, maybe keep this page open as you do it, copying the code as needed into terminal.

 If something does go wrong while doing this, no big deal, if something goes wrong while up grading your BIOS, you have a paper weight, so take it from there.

---

### Post by deadfraggle on 2012-01-28
If the laptop was mine, I may have risked updating the bios.  The laptop also has an unrelated issue with choppy video playback and my friend did not seem too keen on using an MSN Messenger alternative, though he did like Ubuntu's interface.  So I'm installing another OS.

Dang.  Today's bios should have reset to factory options in case of emergency.

---

### Post by pyrforos on 2012-03-01
THANK YOU SO MUCH!This script is the only thing that worked!!:):):)
One question:

From what i have  seen in your code it can be used for any version of ubuntu. Am i right?

---

### Post by Beefy001 on 2012-04-01
> **KidneyBean said:**
> I'm bumping this thread. No why? In the middle of attempting to post my first bump/reply, my Acer 5315 shut down on me. The stupid thing is as hot as an oven- the fan simply isn't kicking on (as usual). 

Now I asked nicely for a reply yet nobody wanted to help. I posted an entire thread about this issue and yet nobody could answer me. 

Right here in this thread the solution to my Acer shut down awaits- but yet nobody can help me out by explaining just why when I type into the terminal the install commands as listed above, that I'm told there is no such file or directory. I unpacked the download. I followed the instructions. PLEASE, what am I doing wrong???

My system is about to shut down again so I'll leave it at this.
after reboot put laptop into suspend and then press anykey to restart,
the problem wont be fixed but your fans should run until you can download the script and sort the problem, hope this helps.

---

### Post by Kogge on 2012-04-03
Fantastic!
It works on my Aspire 5715Z under 10.10 :KS

Thanks!

---

### Post by Capitano Bellodi on 2012-04-22
Hi,
I've just to modify the row 116 of the script as follows to make it consistent with my configuration:
```
  cat /sys/devices/platform/coretemp.0/temp2_input |
```now it works pefectly!

---

### Post by Redonqadonq on 2012-04-27
First time on the forum, and a noob who's just knowledgeable enough to be dangerous: I'll try to keep it concise!

I'm currently running Ubuntu Jaunty on a 5315, celeron, 2g ram. I've tried liveCDs of various distros, and upgrades of Ubuntu, but the fan never kicks in, and the lappy shuts down due to overheating. Jaunty is the only Ubuntu which seems to keep the fan running, but since the repos are dry, I can't update any of the programs -- Jaunty was not an LTS. I read in a different forum post that whatever was in Jaunty that keeps the 5315's fans running was "fixed" (ie, buggered) in subsequent upgrades. The acer_fancontrol fix seems my best bet, as I daren't flash the BIOS -- but I'd like to see if it works first, before I commit to an install, and *then* find out it doesn't work.

So, to the questions:

1. Could the script and mempat and adjustments to startups, etc, be written to a persistent live-USB, so I could test them out first?

2. If not, could they be added to a live-USB or a liveCD as a custom image, and if so, how?

3. Failing all that, what are my options, remembering that flashing a new BIOS is not a preferred option?

Help!

---

### Post by Thulitharn on 2012-07-17
This solution does not seem to work for the 5315 with ubuntu 12.04 LTS.

I have tried a few times now.
Frustrating.  It does not make a newbie want to explore this OS much further.

---

### Post by thequestioner on 2012-07-25
> **Thulitharn said:**
> This solution does not seem to work for the 5315 with ubuntu 12.04 LTS.

I have tried a few times now.
Frustrating.  It does not make a newbie want to explore this OS much further.


in the last step:

"7) Make it run automatically

 	Code:
 	sudo gedit /etc/rc.local 
Insert "acer_fancontrol" before the final "exit 0" (without quotes)."


instead of just having acer_fancontrol, put # acer_fancontrol insted.. this seemed to work for me

(btw i'm a complete noob at this and ive only had ubuntu for a few days, dont be discouraged! :D)

---

### Post by blakekl on 2012-09-03
> **Thulitharn said:**
> This solution does not seem to work for the 5315 with ubuntu 12.04 LTS.

I have tried a few times now.
Frustrating.  It does not make a newbie want to explore this OS much further.

I am also having the same issue on my Acer 5315 on 12.04 LTS. After editing everything i try running ./acer_fancontrol

I get the following output:

$ ./acer_fancontrol
FATAL: Error inserting coretemp (/lib/modules/3.2.0-29-generic-pae/kernel/drivers/hwmon/coretemp.ko): Operation not permitted
You must have module coretemp to monitor the CPU temperature

So it looks like the coretmep module is not installed. Does anyone know how to install this in 12.04 LTS?

---

### Post by blakekl on 2012-09-04
The only way I was able to get around this was to flash the BIOS to v1.43. Relatively painless. Just had to borrow a friends Vista CD, install it and run the BIOS flashing utility available from the acer website. Once it was flashed a clean install of Ubuntu 12.04 LTS was fine with a functioning fan.

---

### Post by keithcochrane on 2012-09-12
I have just used this to fix the fan issue on my old 5315 with 1G, all I had to do was change a line from "temp1_input" to "temp2_input" and it worked great!

Thank you :p

---

### Post by Macksbearflag on 2012-10-14
This works!! Thank you dushmi94, it works on 12.04 . Fan is noisy but it woks and that is the main thing. Flashing the bios is not an option as it will only work with windoze but this solution is safe and simple to execute.Thank you again .  :-)

---

### Post by chansonc4 on 2013-02-03
I'm having this message after doing 
Aspire-5315:~/Downloads/acer_fancontrol$ [COLOR=Red]gedit acer_fancontrol[/COLOR]

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::visited-link-color' of type `GdkColor' from rc file value "((GString*) 0x9393660)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::visited-link-color' of type `GdkColor' from rc file value "((GString*) 0x9a91300)" of type `GString'

what does it mean ?
I'm using Edubuntu on Ebuntu 11.04

---

### Post by LaizureBoy on 2013-04-16
Ok, I'm sure if you are going to read this or not, but here goes:

It's giving you that error because you are not in the right directory. 
Try typing "cd Downloads"
AND THEN
"cd acer_fancontrol"
That should fix your error. Sorry, I would have replied sooner, but I JUST NOW saw your post.

Tell me if I helped!

---

### Post by michaelcranie on 2013-09-25
HI I installed Ubuntu 13.10 64bit this week and am having trouble with the computer overheating psensor shows temp of both cores of my i3 cpu to be high 70-84celsius.

---

### Post by michaelcranie on 2013-09-27
found this [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521) seems to work on most machines can anybody tell me how to find the memory address  my computer has 3gb ram only shows up to 2gb in the  script. installed as 2gb but the computer is still running hot.

---

### Post by YannosB on 2013-09-27
If your CPU's cooking, that may well be a heatsink-to-CPU issue. There is a dialetric paste between the heatsink and CPU, which can (and will) dry up, and break down over time. If this happens, the CPU will begin to keep its thermal heat instead of  leeching it to the heatsink, and the core temps rise. It will murder a CPU and in not too little time.
 If you are not comfortable with opening the box, remounting the heat sink.. most computer repair guy's will be able to do in in half an hour, and the cost should not be high. (I would not pay more than $30 US (including the $6.00 paste)

---

### Post by michaelcranie on 2013-09-28
worked ok under windows this seems to be a problem with aspire computers that used software to control fans in windows. I reformatted to install Ubuntu which wiped this software. Apparently a bios upgrade would fix the problem but i can only find an exe file  and am not sure how to use this with Linux. The script in the link aboveb seems to work but i don't know how to find the correct address for the patch file. Thought Jupiter from the web update ppa might help but doesn't seem to be installable in 13.10

---

### Post by mörgæs on 2013-09-28
You could try to create a live boot USB stick with Freedos. When booted from that you might (can't promise you) be able to run the exe file.

---

### Post by michaelcranie on 2013-09-28
got freedos on usb but not confident about using it, afraid i'll brick the laptop.  The link in my second post seems to say better to get the script running

---

### Post by mörgæs on 2013-09-28
I think the best you can do is to post in the other thread. Seems to be a lot of experienced people there. 

I can move your thread if you want to.

---

### Post by michaelcranie on 2013-09-29
Yes please move the thread. looked at the script doesn't seem to work on 13.10

---

### Post by mörgæs on 2013-09-29
Done, good luck.

---

### Post by eh3avon on 2014-01-15
thanks for help!!!!
that worked perfectly to my 2gb ram acer !!!!  :)

---

### Post by isla on 2014-02-18
i'm a newbie....reall newbie...

at the beginning ofthe firstpost it says download the script. please can you tell me what script and where?
thankyou

isla

---

### Post by isla on 2014-02-18
i've got as far as the last couple of instructions but when i try to move the files to bin - i get this message
cp: omitting directory `acer_fancontrol'
ila@computeris:~/Downloads$ 
ila@computeris:~/Downloads$ sudo gedit /etc/rc.local


i run the file locally and it pops up and says 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
acer_fan control
exit 0

as you can see i've entered the last command as instructed but i do not know what to do next. i close the file. close the terminal and nothing happens after that...not sure how this is meant to work.?

any helps would be great thanks = i started a new post but thought i might get directed here...

---

### Post by trickster3 on 2014-06-11
Just wanted to say thanks to OP, this worked for me on Acer Aspire 5315 on Ubuntu 14.04 LTS. Cheers !

e2a: grrr, after reset fan is not working again... gotta research further...

another e2a: so, after researching further, it seems only bios update does the trick... so i installed Win, updated BIOS, reinstalled Ubuntu,
and bingo. Fan works. Hope it helps someone.
Cheers.

---

### Post by mathiola2 on 2014-09-20
Depois de 2 anos de muita pesquisa e muito trabalho tentando solucionar o problema do cooler que não ligava no meu acer aspire 5315-2290 com ubuntu 12.04, finalmente foi solucionado com esse tutorial. Foi só seguir o passo a passo e funcionou corretamente. No começo eu achei que não tinha dado certo pois quando liguei o notebook, o cooler ficou desligado, mas quando estava atingindo a temperatura máxima em que ele desligava sozinho, eis que "magicamente" a ventoinha ligou sozinha. Fiquei até emocionado! Vale a pena criar a conta para se logar e baixar o arquivo.

After two years of extensive research and hard work trying to solve the problem did not care of the cooler on my acer aspire 5315-2290 with ubuntu 12.04, was finally solved with this tutorial. It was only following the step by step and it worked correctly. At first I thought it had not worked because when I turned on the notebook, the cooler was turned off, but when I was reaching the maximum temperature at which it hung up alone, behold "magically" turned the fan alone. I was so thrilled! Worth creating the account to log in and download the file.

Después de dos años de investigación y trabajo duro tratando de resolver el problema no se preocupan de la nevera en mi acer aspire 5315-2290 con ubuntu 12.04, fue finalmente resuelto con este tutorial. Sólo estaba siguiendo el paso a paso y funcionó correctamente. Al principio pensé que no había funcionado porque cuando encendí el ordenador portátil, el refrigerador estaba apagado, pero cuando estaba llegando la temperatura máxima a la que se colgó solo, he aquí "mágicamente" la vuelta al ventilador solo. Estaba tan emocionada! Creando Worth la cuenta para iniciar sesión y descargar el archivo.

---

