---
title: "two-finger option in the prefrences&gt;mouse is greyed out"
date: 2010-08-03
forum: Hardware
---

### Post by pareshverma91 on 2010-08-03
Hi all,
The two-finger scrolling works great on my windows7 partition but i am unable to figure out why the two-finger scrolling option in the system>preferences>mouse is greyed out.
I have checked out other threads in this forum regarding making the two-finger scroll work but all have tried to make up a script and run that at the startup. I am a bit unsure of that. 
Can anybody help me with the two-finger scroll.
(Installed touchpad from repositories but it has no option)

---

### Post by chilloutmo on 2010-10-10
same problem here. works fine in W7, even zooming and those other advanced multi-touch functions but in ubuntu it doesn't. thought the problem would be solved with 10.10, but after today's update the two-finger scroll checkbox is still gray. i tested unity but it's also not working. i have a asus 1215n running 10.10.

---

### Post by j0lle on 2010-10-12
same problem here.
asus eee pc 1005PE

---

### Post by High__Flyer on 2010-10-12
I've also got the same problem, The thing is, there's a script out there that will enable it, but it's not persistent, and will disable after sleep.
I'm new to Linux and being used to windows, I'm used to downloading a file that would *make it work*

Is there any Simple way to get two finger scroll working?

---

### Post by irv on 2010-10-12
So far 4 users are having this problem, but there was no mention of what machine there are using. I have a Dell Inspiron 1521 and it is working on my machine. Maybe you can tell what machine you are using because the problem could be 10.10 has a bug with your hardware. Or maybe a driver issue. You have to start somewhere to pin point the problem.
The point being if it is working on some machines and not other that need to be known.

---

### Post by High__Flyer on 2010-10-13
Samsung NC10 For me

---

### Post by Papex on 2010-10-14
I also have this problem. I'm on an Acer Aspire 5739G.

Every time I put a second finger on the touchpad my pointer goes crazy.

This issue really reduces the joy of Ubuntu.

---

### Post by chilloutmo on 2010-10-14
As I already mentioned I am using a Asus 1215n and Ubuntu 10.10, but it didn't work under 10.04 either. It seems that many people with lots of different machines seem to have this problem. Can anyone please help ?

---

### Post by infinite012 on 2010-10-14
Try typing this into terminal

```
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```

It works for me to get back my two finger scrolling that is so easily found in Windows 7.

My only problem is putting this into a start up script. I'm a complete newbie to Ubuntu/Linux in general, so I just bound the F1 key to execute this little bit of code for the time being.

---

### Post by k.bendy on 2010-10-14
now the screen doesnt stop scrolling up n down

---

### Post by infinite012 on 2010-10-14
Are you using a Synaptics touchpad? I also ran another script before the one I posted to force Ubuntu to select "two-finger scroll." I'll try and find out what I used.

Edit: This link is sort of what I'm talking about, with the second code box. Although I didn't type nearly as much.

[http://ubuntuforums.org/showthread.php?p=9966007](http://ubuntuforums.org/showthread.php?p=9966007)

---

### Post by Valentini on 2010-10-26
The command you are looking for is this one:
```
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type int "2"
```

---

### Post by dm1027 on 2010-12-21
Sorry to resurrect this thread, but I am having the same problem on a Toshiba L645 D. I used the scripts above, and now in my mouse preferences "Two Finger Scrolling" is still greyed out but is now ticked as being selected.

2 finger scrolling is not working either. 

Toshiba L645D and Ubuntu 10.10

---

### Post by godfazr on 2010-12-21
dm1027 - check this post [http://ubuntuforums.org/showpost.php?p=10071212&postcount=8](http://ubuntuforums.org/showpost.php?p=10071212&postcount=8)
just tried this and it seems to work.

however, i'd like to know if it's possible to make other multi-touch features work? i.e. my Acer AO751h supports also two finger zoom and horizontal scroll, so it would be nice to get them working too (however, it's not critical since I rarely use horizontal scroll and never used zoom).

---

### Post by dm1027 on 2010-12-21
I also have a 751h netbook. I tried to get all these things working, but I never could.

Let me know if you figure anything out

---

### Post by dm1027 on 2010-12-21
By the way, that link you provided worked great. Thanks! Your help is appreciated

---

### Post by vedster on 2011-01-17
> **infinite012 said:**
> Try typing this into terminal

```
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```It works for me to get back my two finger scrolling that is so easily found in Windows 7.

My only problem is putting this into a start up script. I'm a complete newbie to Ubuntu/Linux in general, so I just bound the F1 key to execute this little bit of code for the time being.

1. Open gedit
2. Paste your code in (It's actually the same as mine :p)
3. Save the file in your home directory as multitouch.run
4. Go to System>Preferences>Startup applications
5. Add the (.run) file to the list.

Hope this helped!

NOTE: I'm a new Linux/Ubuntu user too, but I found this out a couple hours ago and so far has worked for me :)

---

### Post by balta on 2011-04-22
EDIT: not working

> **Valentini said:**
> The command you are looking for is this one:
```
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type int "2"
```
Hi there,
 this is just perfetc. Exactly what I was looking for, no scripts no packages to install. Works perfectly on my 10.04.
I'd just like to add that you can also use the GUI provided by
```
gconf-editor
``` (can be run from terminal or by the ALT+F2), browse to ```
/desktop/gnome/peripherals/touchpad 
``` and tweak everything you wish to.

EDIT 2: only working solution found is in post above this by vedster. thanks.

---

### Post by shoaib77 on 2011-09-12
Hi all,

I've been having the same issue as most people here (about the greyed out "Two finger scrolling"). I did what vedster said to do yesterday and it worked fine. But I tried it again today and it doesn't work. I also created the .run script file in his instruction, but the script never ran. I'm not too familiar with writing scripts; but after doing a bit of reading I found a tutorial and tried writing the script that way- "#!/bin/sh... etc" - but it stll didn't work.

My laptop is an HP Pavilion dv5 1050ee

Any help would be much appreciated

---

### Post by goblin_ax on 2011-10-31
synclient VertTwoFingerScroll=1 synclient HorizTwoFingerScroll=1 synclient EmulateTwoFingerMinW=5 synclient EmulateTwoFingerMinZ=48

I tried that but I get this message: Couldn't find synaptics properties. No synaptics driver loaded?
I have a Samsung RF410 and it does have a synaptics touchpad.
Also, on kubuntu the 2 finger scrolling works fine.

---

