---
title: "tackling the screen brightness problem"
date: 2008-05-22
forum: Hardware
---

### Post by priegog on 2008-05-22
So the thing is this. I have 2 laptops, neither of whose screen backlights can be changed via the display brightness applet. One of them has a keyboard, alongside with the brightness keys so I couldn't care less abut that one, but the other one is a tablet which lacks brightness buttons. Under windows the only way to change it is via a program that does it, so I know it's possible to do so. 
So I have been researching, and found the whole /proc/acpi/video/~/brightness thinguie. The thing is, even if I start a root session I can't open that file with either gedit or nano. So I guess the real question is: How do I read/write to that "file"?

---

### Post by didac on 2008-05-22
Check

[http://ubuntuforums.org/showthread.php?t=583752](http://ubuntuforums.org/showthread.php?t=583752)

for a solution. Another workaround is to use xgamma. Create a file called myxgamma or whatever you like it called, and write:

```
/usr/bin/xgamma -rgamma 0.7 -ggamma 0.722 -bgamma 0.75
```

These are my values. You can experiment with them. Read man xgamma

Make it executable:

```
chmod +x myxgamma
```

and double-click on it, execute it. To make it work at every reboot, add it to System >> Preferences >> Sessions

I know, gamma is not brightness, but I kill two birds with the same stone.

---

### Post by priegog on 2008-05-22
> **didac said:**
> 
I know, gamma is not brightness, but I kill two birds with the same stone.Exactly, but thanks.
that other thread you gave me is a good way of executing what I want to do; but to do that I first need to figure out the min-max values allowed to set it. And for that I need to read the file. and I can't do that.

---

### Post by didac on 2008-05-22
Sorry, I have a chip card that doesn't allow such possibilities. Cannot replicate your problem. Does your file already exist? Who owns it? Do a ls -l to know. And become superuser by running sudo -s As superuser you should be able to cat the file.

The values should be anything between 0 and 100

Most likely you already knew all that. Just in case. Sorry for being a bore. :)

---

### Post by priegog on 2008-05-22
Not at all. So let's see. the file does exist and apparently root owns it ```
-rw-r--r-- 1 root root 0 2008-05-22 14:42 /proc/acpi/video/VGA/LCD/brightness
``` (no surprises there). I didn't know about the cat command, but if I use it on that file, either as a normal user or as a super user I only get the output <Not Supported>

Also, what do you mean by "I have a chip card that doesn't allow such possibilities"? Is that possible? How would I know if that was my case? My video card is an intel integrated (part of the earlier centrinos). Also, the fact that the brigtness can be controlled in Windows makes me think it should be possible to make that call from software. Just out of curiosity: how do you change YOUR brightness?

---

### Post by priegog on 2008-05-22
Hey! I just got something on the other laptop (the one that matters, but I was testing things on this one since the other one doesn't have a keyboard.) Anyways, the output of the file is ```
levels: 8 6 0 1 2 3 4 5 6 7 8 9 10
current: 0
```So apparently the levels go from 0 to 10 (don't know what that 86 is all about there, but whatever) Could you please explain to me the syntax of the echo command to modify that? from there on I think I can find my way.
Also, I read somewhere that sudo wouldn't work with that echo command, so how would I go about creating a script for that? Also, any suggestions on said script? Should I make 10 different scripts, or can I have it ask me what value would I want? or even better, sync that thing with the gnome brightness applet? I know it's a lot of questions, so thanks in advance :)

---

### Post by didac on 2008-05-22
So in the case of your laptop the values go from 0 to 10. The command will look like:

```
sudo -s
echo -n 5 > /proc/acpi/video/VGA/LCD/brightness
```

Now, the path may be different in the other laptop, maybe instead of VGA you'll have SVGA or whatever. The syntax only changes in the 5. There you experiment with different values.

Also, you have to do a 

```
 ls -l /proc/acpi/

```

Maybe you don't have writable permissions in that folder and that's why you cannot echo anything into brightness, even though brightness is writable, as I can see from your ls -l

Regarding the script, the link in Ubuntu forum you already know:

[http://ubuntuforums.org/showthread.php?t=583752](http://ubuntuforums.org/showthread.php?t=583752)

explains how to go about it. There is a mistake, though. It's not sudo visudo
but

```
sudo vi /etc/sudoers
```

or, more comfortable

```
sudo gedit /etc/sudoers
```

to change your permissions about what sudo can do.

If you know a little of C language, you can make a script that asks you for input, or put it as an argument to the command line. In that way you avoid 10 scripts.

My card is a cheap ATI. I control brightness with xgamma, by reducing or increasing values. Not even Windows allows me to do it through software. As for your card, being Intel, maybe somebody has thought a solution. I don't think Intel will think about it, no offense intended against them. Maybe there is something in the Sourceforge or Freshmeat, just a wild shot, have no idea.

---

### Post by priegog on 2008-05-22
thanks a bunch, I was going crazy with vi. gedit is much simpler. I think I can take it from here.

---

### Post by didac on 2008-05-22
Zorionak. Instead of vi try nano for editing from the command line.

---

### Post by priegog on 2008-05-22
haha oh wow. have you visited us in the basque country? eskerrik asko

---

### Post by didac on 2008-05-22
Nope. I live in Nigeria and my colleague sitting near by is a Basque doctor, by name Machimbarrena, who just gave me the tip. I've cheated.

---

### Post by priegog on 2008-05-22
Nice. I'm studying medicine in the EHU (probably where he did too). Thanks a bunch anyways.

---

