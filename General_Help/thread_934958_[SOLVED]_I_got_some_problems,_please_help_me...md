---
title: "[SOLVED] I got some problems, please help me.."
date: 2008-10-01
forum: General Help
---

### Post by sadak on 2008-10-01
I've got some problems..
1.my cpu usage is veryyyyyyyyy high,even when i am not using heavy application,in windows everything is fine...I've just started to love ubuntu because of its fresh design,but this cpu usage do sucks.....

2.when I try to save a file (I am using ubuntu ) in a partition, then when I opened it when i am using windows, then the file is gone,in some cases it says that it is corrupted....
however, when I save a file (now I am using windows), then when I use ubuntu to open it, it works...I wonder, what is the prob?

3.in windows, when we saw a video in youtube, the file is automatically cached in our system,so when we want to get the file,what we need is only to go cache folder, search for the vid and rename it...
can we possibly do the same thing with linux especially ubuntu?

4.I can't play warcraft, is there any way I can play the game in linux ubuntu   without reinstalling the warcraft again?

5. in windows version, when we are using the internet, there's a simple icon in our taskbar and when we click on it, they will show our internet time usage, can i possibly find the same function of it in ubuntu??if yes, please tell me??

6....I've got a lot more question coming up, but I just can't think of it now, so I hope that you will help me...because I am a newbie!

---

### Post by ju2wheels on 2008-10-01
1. Please tell us what type of hardware setup you have (cpu type, ram, video card etc).

2. Try running fsck to see if there are file system errors or corruptions that can be corrected.

3. Yes there is a program designed specifically to download and save youtube videos. Open a terminal and type the following:
```

sudo apt-get install youtube-dl

```
Then to download a video just use the Youtube link:
```

youtube-dl http://www.youtube.com/blablabla

```

4. Yes you should be able to play warcraft on Linux, but you will have to reinstall it on ubuntu. See winehq.org for more details.

---

### Post by Sycron on 2008-10-01
```
3.in windows, when we saw a video in youtube, the file is automatically cached in our system,so when we want to get the file,what we need is only to go cache folder, search for the vid and rename it...
can we possibly do the same thing with linux especially ubuntu?
```

The flv files are cached in **/tmp** folder.

---

### Post by sadak on 2008-10-01
Pentium(R)4 CPU 2.66GHz 
384MB RAM (I do not know what is happening with my ram, as far as i know,I had the 512 mb )

and by the way, which one do you prefer on linux ubuntu,firefox or opera?

---

### Post by sadak on 2008-10-01
> **ju2wheels said:**
> 
2. Try running fsck to see if there are file system errors or corruptions that can be corrected.

here's the output 
> fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=56c435e1-40de-4fa9-81c4-eae5a5cfe8fb'


---

### Post by oldos2er on 2008-10-01
"when I try to save a file (I am using ubuntu ) in a partition, then when I opened it when i am using windows, then the file is gone,in some cases it says that it is corrupted...."

 Windows cannot read ext2 or ext3 partitions natively. I believe there is a program or plugin of some kind available for download that will allow it to do so. Google's your friend here.

---

### Post by Sycron on 2008-10-02
To see ext2 and ext3 partitions in Windows you can use fs-driver [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sadak on 2008-10-02
thanks for all your help...

by the way, how about the problem of my high cpu usage>>??? is there any solution?

---

### Post by TheLions on 2008-10-02
type "top" in terminal and tell us what is using CPU (+20%) or put a screenshot!

---

### Post by sadak on 2008-10-02
here's the attachment..
F.Y.I: when I close all the application like Firefox and when I open the system monitor, the CPU usage always fluctuate...
Kind of different with windows, when I don't do anything..they just go flat...

---

### Post by TheLions on 2008-10-02
firefox is draining a lot of CPU, install  swiftweasel to solve this

about minor(<10%) CPU usage, that is normal

---

### Post by sadak on 2008-10-03
oke,that really helps!!!!
thanks.....!!!!!!!!!!!!!!!!!!1:o
:KS:KS:KS:KS:KS for all of you!!!!

btw,here's another problem...
When I try to stream a video from youtube and play a song from vlc,somehow, I can hear the sound... Sometimes, I can only hear the sound of the video I am streaming,sometimes I just can hear it from my vlc player,but in some cases, I can't hear both...

what's the prob?

---

### Post by Ryadt on 2008-10-03
Do```
killall pulseaudio
```
Then go in System > Preferences > Sounds and switch everything to ALSA.

---

### Post by sadak on 2008-10-03
that also helps,but must I do it everytime I login to linux??

---

### Post by Calmatory on 2008-10-03
I'd love to hear a automagick workaround for this. Though, I am quite sure that proper pulseaudio/ALSA configuration might help, there are people who just don't have one configured properly. :p So, if there is a permanent workaround, someone care to share? Even cronjobing killall pulseaudio would be great unless it causes problems.

---

### Post by Zaff on 2008-10-03
> **Calmatory said:**
> I'd love to hear a automagick workaround for this. Though, I am quite sure that proper pulseaudio/ALSA configuration might help, there are people who just don't have one configured properly. :p So, if there is a permanent workaround, someone care to share? Even cronjobing killall pulseaudio would be great unless it causes problems.

Install libflashsupport
```
sudo apt-get install libflashsupport
```
Or go to adobe's website and get Flash 10 for linux (it's unstable at the moment I think).
This should solve the pulseaudio / Flash incompatibility.

---

### Post by Sycron on 2008-10-03
The pulse audio problem was getting on my nerves 2 weeks ago. Now I'm glad I fixed it.

---

### Post by sadak on 2008-10-03
ow,again thanks....

btw, again , is there any tool that can show me how long have I been surfing the internet, something like knowing my internet time usage? 

again, another question,in windows ,when we open task manager then it lists all the active processes, however in linux,when i use system monitor, there's either the word:  sleeping or running??what is it? can I just end the processes that is sleeping? are there any recommendation on the processes that might not be useful for me,or maybe the one that is rarely used?

---

### Post by Ryadt on 2008-10-03
Please mark this thread as solved.
Start new threads for new queries.

---

### Post by /////// on 2008-10-03
You could put "killall pulseaudio" in the rc.local file and reset its permissions. After this, the command will run everytime you start up your computer but then youd still have to "go in System > Preferences > Sounds and switch everything to ALSA."

---

### Post by 3rdalbum on 2008-10-03
"Sleeping" just means that it's not using any CPU time at that particular moment. Multitasking works by the operating system distributing CPU access to programs many times per second. In reality, only one program can be using the CPU at any one time.

So DON'T kill something just because it's showing as "sleeping"! It might be sleeping every time the list updates, but it's probably doing important stuff very quickly each second.

---

