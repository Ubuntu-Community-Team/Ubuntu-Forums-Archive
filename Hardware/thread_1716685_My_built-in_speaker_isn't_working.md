---
title: "My built-in speaker isn't working"
date: 2011-03-28
forum: Hardware
---

### Post by NotYetReady on 2011-03-28
Greeting Ubuntu folks! 

I'm using ASUS K42F device, running Ubuntu 10.10 desktop 32-bit on it.
My problem is that my built-in speaker isn't working, but... surprisingly when I plug in my headphone works wonder.


Thanks in advance.
NotYetReady.

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by akshaykumrawat0 on 2011-08-07
I m also facing the same problem-
 my built-in speaker isn't working, but surprisingly when I plug in my headphone works wonder.

So pease someone can give solution for the same.

Regards,
AK

---

### Post by lidex on 2011-08-16
> **akshaykumrawat0 said:**
> I m also facing the same problem-
 my built-in speaker isn't working, but surprisingly when I plug in my headphone works wonder.

So pease someone can give solution for the same.

Regards,
AK

See post #2

---

### Post by hansdown on 2011-08-16
lidex = ROCK.

---

### Post by johntland on 2011-08-22
I am having a similar problem. Only one of my speakers is working and the headphones are not working. I am BRAND NEW to Ubuntu and Linux in general. I did follow some instructions and got a TON of data for someone to check out if they can help. It is located at: [http://www.alsa-project.org/db/?f=061b6b923902602d441629b4cfca0a135b5a2145](http://www.alsa-project.org/db/?f=061b6b923902602d441629b4cfca0a135b5a2145)


Any help will be appreciated!

JTL

---

### Post by lidex on 2011-08-22
> **johntland said:**
> I am having a similar problem. Only one of my speakers is working and the headphones are not working. I am BRAND NEW to Ubuntu and Linux in general. I did follow some instructions and got a TON of data for someone to check out if they can help. It is located at: [http://www.alsa-project.org/db/?f=061b6b923902602d441629b4cfca0a135b5a2145](http://www.alsa-project.org/db/?f=061b6b923902602d441629b4cfca0a135b5a2145)


Any help will be appreciated!

JTL

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by johntland on 2011-08-22
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
options snd-hda-intel model=laptop position_fix=1 enable=yes
john@john-Laptop:~$ 

is what came back, however it didn't fix it. :(

---

### Post by lidex on 2011-08-24
OK. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by johntland on 2011-08-24
> **lidex said:**
> OK. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Nope.....

---

### Post by lidex on 2011-08-28
Since the edit to alsa-base.conf is not working, remove it
and see this post:
[http://ubuntuforums.org/showpost.php?p=11114071&postcount=60](http://ubuntuforums.org/showpost.php?p=11114071&postcount=60)

---

### Post by Montse45 on 2012-02-07
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


I am a new user of ubuntu. And I had also this problem:
"My problem is that my built-in speaker isn't working, but... surprisingly when I plug in my headphone works wonder."

I read your answer and execute de wget command. What should I do now?

---

