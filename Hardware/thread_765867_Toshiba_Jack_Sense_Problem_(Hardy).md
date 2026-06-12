---
title: "Toshiba Jack Sense Problem (Hardy)"
date: 2008-04-24
forum: Hardware
---

### Post by crusher_of_c on 2008-04-24
Hi,

I am using a Toshiba Satellite A 200 AH 9 with a Realtek ALC861-VD sound card. I have just installed Hardy and am having problems with my sound output. Sound works on both my laptop and headphones at the same time. There seems to be no jack sense. I have encountered this problem and possible solutions with other Ubuntu versions, but there seems to be no documentation for Hardy. I am a fairly new user so please try and explain anything I have to do with plenty of description. Thank you in advance for any help.

---

### Post by RandyNose on 2008-05-26
Yea, I have a Toshiba Satellite A135-S4656 with a, Realtek ALC861-VD intel sound chip.  I have the same problem, I also have 8.04 installed, and to get the headphones to put anything out, I had to add the line

```
 sudo gedit /etc/modprobe.d/alsa-base 
```

Add this line to get the headphones to put sound out. 

```
options snd-hda-intel position_fix=1 model=3stack
```

There is a post over here... 

[http://ubuntuforums.org/showthread.php?p=4826100&highlight=Realtek+ALC861-VD#post4826100](http://ubuntuforums.org/showthread.php?p=4826100&highlight=Realtek+ALC861-VD#post4826100)

That has one re- compiling, haven't given it a shot as of yet, I don't have the time at the moment, if it breaks things, to fix things.  I went through a mess with Feisty to get it going, and don't feel up to it at the moment.

---

### Post by wzf851005 on 2008-05-27
These patterns are based on different foot type, weight, Speed, training programmes, gender and skill level design. These different styles, different prices and multi-purpose products, attracting hundreds of thousands of jogging, making them feel that [nike shoes](http://www.bestbuynike.com) is to provide the most complete variety of running shoes manufacturers, millions of range of ability Running to have that belief.   First-generation jordan shoes uppers, there is a conspicuous "Chachi basketball" signs in the use of trapeze signs ago, the first generation and second generation Chachi Jordan basketball shoes are used as signs. First-generation[jordan shoes](http://www.pickyourjordan.com) appeared in 1985, 1994 and 2001 NIKE companies produced twice again this shoes. For the classic colors with a red, black, and compared with black. [Air Jordans](http://www.oknike.com), published in 1991, jordan shoes91-92 season Zhanxue because jordan shoesin the Barcelona Olympic Games 92 wearing this pair of 7 and winning the title, the seventh generation in jordan shoesin the series, it is particularly valuable. 7 and the shape of the shadow of some six generations, the biggest feature is particularly color.  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.

---

### Post by ginjabunny on 2008-06-11
I have a Toshiba Satellite L30-10V with ALC861-VD and I have had problems with 7.10 and 8.04, I could either get the speakers to work or headphones but not both at the same time and the headphones didn't override the speakers.

I have now GOT IT WORKING properly (hurrah), this is what I did, it failed when run with sudo so I had to enable root and logon to get this to work (do - sudo passwd root, and enable root login on the login window), in terminal run

apt-get install module-assistant

module-assistant a-i alsa-source

... then reboot

now when I open volume control I have "HDA ATI SB (alsa mixer)" when I change device and I have headphone and speaker sliders in it and both work and speakers cut out when headphones are plugged in.

Hope this helps :)

it also worked (hurrah)  on on my Asus Pundit which has a ALC861 chipset

---

### Post by robboguy on 2008-07-06
Thanks ginjabunny, I can confirm your fix worked for my Toshiba A300/M00

---

### Post by sixblades on 2008-07-25
**@ginjabunny:**
Rather than allowing root logon you could just login to a root shell. Open up a terminal and type ```
sudo su
``` Enter your password. You are now "logged in" as root!

---

### Post by phidia on 2008-07-25
> **ginjabunny said:**
> I have a Toshiba Satellite L30-10V with ALC861-VD and I have had problems with 7.10 and 8.04, I could either get the speakers to work or headphones but not both at the same time and the headphones didn't override the speakers.

I have now GOT IT WORKING properly (hurrah), this is what I did, it failed when run with sudo so I had to enable root and logon to get this to work (do - sudo passwd root, and enable root login on the login window), in terminal run

apt-get install module-assistant

module-assistant a-i alsa-source

... then reboot

now when I open volume control I have "HDA ATI SB (alsa mixer)" when I change device and I have headphone and speaker sliders in it and both work and speakers cut out when headphones are plugged in.

Hope this helps :)

it also worked (hurrah)  on on my Asus Pundit which has a ALC861 chipset

Thanks for this! I ran those commands and rebooted but there is still no main speaker muting on my laptop :(

I have a HP pavilion with the same problem-although main speaker muting-with headphones plugged in works in opensuse 11 without any additional configuring.

---

### Post by hotweiss on 2008-07-25
> **crusher_of_c said:**
> Hi,

I am using a Toshiba Satellite A 200 AH 9 with a Realtek ALC861-VD sound card. I have just installed Hardy and am having problems with my sound output. Sound works on both my laptop and headphones at the same time. There seems to be no jack sense. I have encountered this problem and possible solutions with other Ubuntu versions, but there seems to be no documentation for Hardy. I am a fairly new user so please try and explain anything I have to do with plenty of description. Thank you in advance for any help.

You can try this solution here:

[http://www.immv.es/index.php?page=linux-on-a-toshiba-a200-12x](http://www.immv.es/index.php?page=linux-on-a-toshiba-a200-12x)

And this one here:

[http://personales.ya.com/ambeon/toshiba.html](http://personales.ya.com/ambeon/toshiba.html)

---

### Post by shadybones on 2008-10-01
my problem - headphone out doesn't work
fixed by adding the mode=3stack to the hda option

my new problem - speakers won't stop when headphone is plugged in

I'm new to linux, so if something requires more than copy/paste then it's beyond me, but I've done all that this thread suggests on my satellite A135-S4666, to no avail. as for what's not listed here, I've tried various alternatives I've found on the web for the option entry into alsa-base, but they all seem like different ways to do the same thing. the commands:

sudo su
alsa force-unload
modprobe snd-hda-intel

came in handy to try out a new configuration of alsa-base without restarting (as I said, I just copy/paste and believe anything I'm told).
I've even re-compiled the alsa-source with the module-assistant and all that, without success.
My Hardy is a fresh install and up to date.
I'd appreciate a contact from anyone else with a A135-S4666 or closely related model about this issue.

---

### Post by pauix on 2012-01-04
> **ginjabunny said:**
> I have a Toshiba Satellite L30-10V with ALC861-VD and I have had problems with 7.10 and 8.04, I could either get the speakers to work or headphones but not both at the same time and the headphones didn't override the speakers.

I have now GOT IT WORKING properly (hurrah), this is what I did, it failed when run with sudo so I had to enable root and logon to get this to work (do - sudo passwd root, and enable root login on the login window), in terminal run

apt-get install module-assistant

module-assistant a-i alsa-source

... then reboot

now when I open volume control I have "HDA ATI SB (alsa mixer)" when I change device and I have headphone and speaker sliders in it and both work and speakers cut out when headphones are plugged in.

Hope this helps :)

it also worked (hurrah)  on on my Asus Pundit which has a ALC861 chipset

That did not work for me, but thanks for the information!

---

