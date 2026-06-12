---
title: "Question about fglrx"
date: 2013-05-01
forum: Hardware
---

### Post by pantabulosin on 2013-05-01
Greetings.

I was looking at the software center and I notices that in Edit > Software Sources > Additional drivers there was an option to use the proprietary drivers for AMD cards. I've already tried looking at the proposed ways to install the proprietary driver and so far they involve a lot of blindly pasting commands and the risk of Unity not running/booting in low resolution mode, so I was wondering if those tutorials are outdated and using the software center is a viable alternative.

Also, I think it's worth asking if going through this will actually work with my card. I have an AMD Radeon H 7670M and an Intel 4000 HD if I recall correctly.

Thank you for your time

---

### Post by ppjdee on 2013-05-01
I have installed the latest ati driver from amd.com for my gfx card under 13.04. So far it worked well, I used the .deb to install using the link below to aid me :D
There could always be a risk of Unity crashing when installing ati drivers, so I would keep some terminal commands close by incase you have to remove them.
[http://www.youtube.com/watch?v=U1kanjD4qgo&lc=bMppJhcPy1sEtvxsaLNONzLnOnGYQQQwqM0HrDfdRHg](http://www.youtube.com/watch?v=U1kanjD4qgo&lc=bMppJhcPy1sEtvxsaLNONzLnOnGYQQQwqM0HrDfdRHg)

---

### Post by pantabulosin on 2013-05-01
Thanks for replying, I'll take a look and try it.

---

### Post by pantabulosin on 2013-05-02
So I tried what the video said but I ran into a problem: Ubuntu raring goes directly to gedit without asking me if I want to run the program and then gedit hangs.

So I tried the "Additional drivers" section of the Ubuntu Software Center and upon rebooting Unity stopped working properly (no dash/panel, no global menus, no alt-tab, no upper bar to move windows). It's a good thing that ctrl +alt + t worked and stuff like the network manager worked too.

At any rate, I followed the guide here [http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers) but now only my gnome-shell session works. Unity is just as bad. 

Is there any way to go back to defaults without reinstalling? I haven't done much but it would be faster if there a CLI way of getting rid of this issue.

Thanks again for your help

---

### Post by ppjdee on 2013-05-02
To fix the gedit issue(cerdit to myromance or w/e :D) go to file>preferences>behavior>exe.text files tick "ask each time". Then on the gfx driver .deb right click>properties>tick run as exe.
Should install correctly after that.

try ```

sudo apt-get remove --purge fglrx fglrx-amdcccle
or
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```
Then reboot. It should bring Unity back.

---

### Post by Mark Phelps on 2013-05-02
You appear to have AMD/Intel Hybird Graphics -- a very difficult situation.  You can't install drivers from AMD because they will not work.

You will have to read through the thread to see what solutions, if any, will work for you:  [http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450")

---

### Post by pantabulosin on 2013-05-02
Thanks for the help. Unfortunately, the code you posted did not bring Unity back.

Also, I still can't run the file from AMD because I have to run it as a super-user and even though I give it my user password at the start it seems to crash. I've tried running it on the terminal as well to see what output it has and the terminal just closes unexpectedly.

Any ideas? I'll appreciate any input on the matter.

---

### Post by ppjdee on 2013-05-02
Yeah, I missed the Intel part lol. Mark Phelps's link should help you.

---

