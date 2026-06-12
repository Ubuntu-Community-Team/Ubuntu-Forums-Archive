---
title: "Several Problems"
date: 2008-07-11
forum: General Help
---

### Post by [Jaguar] on 2008-07-11
Hey there,

I've found a pretty old CD here on my desk when i was moving, I inserted it on the drive and it was the 64Bits Ubuntu 7.10. So I was like "Cool, I gotta install it to see how it works"

Meh, it isn't what i expected but i like to use it to browse around since it's way safer than Windows. So here goes the problem list:

1 - The first I noticed; I've got a LG Flatron L1550S 15'' (I use it on 
office) that only goes to 1024x768 and apparently the boot screen is 1280x1024 ( it is able to show on a 17'' Monitor ( My houz' monitor ) ). Not huge problem but pretty annoying, is there any fix?

2 - I couldn't install nVidia's restricted driver, so I've gone to "Add and Remove" and installed manually the driver. So far so good but when i was changing resolutions, it only goes to 1024x768 ( it could go to 1280x1024 with "default" drivers ) and shows completely wrong refresh rates, like, on 1024x768 it shows "50Hz, 51Hz, 52Hz" BUT on the LCD's monitor menu it shows on 50Hz as 60Hz, 51Hz as 75Hz and 52Hz as 70Hz. Pretty damn annoying.
(Onboard nVidia GeForce 6100 MCP61 shared 128MB )

3 - Ubuntu shows my computer as 1000MHz! It's a AMD Athlon X2 4000+ with a overclock to 4800+ (2513MHz) with Cool n' Quiet enabled, but even with CnQ enabled, it runs @ 1210MHz! Should I disable CnQ? I frequently use it on Windows when I'm downloading big files over the night, to save energy.

4 - The toolbars ( both Top and Bottom ) keeps disorganizing, messing up icons around like putting the Shut Down button ( the red one ) to the middle of the toolbar. Why is that happening?

5 - Window tops ( the one that includes the window title, maximize, minimize and close buttons ) keeps disappearing, or turning on the window color ( Like now I am using Firefox, it's silver and I use the window top as Brown, it keeps changing colors to silver ) but if I hover the mouse on it, it turns brown back.

6 - My Microsoft IntelliMouse side buttons won't work. How can i set it to back and forward?

7 - How can i set manually the CPU affinity? the "taskset" cmd is pretty annoying and hard (For me) to use

That's all for now.

And i have a suggestion...

 Can i set for every desktop, one processor? ( Like on the bottom toolbar i can change two desktops, can i set one processor for each desktop? ) ( You may think: If the window is between the desktops? Well, it may use both processors.. )

And a question..

Is there any cool racing/shooting game for Ubuntu?




Thanks for reading. Hope you know how to fix at least one problem.

---

### Post by Titan8990 on 2008-07-11
> 
3 - Ubuntu shows my computer as 1000MHz! It's a AMD Athlon X2 4000+ with a overclock to 4800+ (2513MHz) with Cool n' Quiet enabled, but even with CnQ enabled, it runs @ 1210MHz! Should I disable CnQ? I frequently use it on Windows when I'm downloading big files over the night, to save energy.

You should **always** turn off CnQ or Speedstep when overclocking. Unless of course you want an unstable system.

It is known that the usual Linux utilities don't recognize your overclock but I can assure you that your system is still OCed to what you specified in your BIOS.

---

### Post by [Jaguar] on 2008-07-11
> **Titan8990 said:**
> You should **always** turn off CnQ or Speedstep when overclocking. Unless of course you want an unstable system.

It is known that the usual Linux utilities don't recognize your overclock but I can assure you that your system is still OCed to what you specified in your BIOS.

Thanks for the answer.

Actually the system doesn't get unstable when using overclock, I've did several tests like opening 'heavy' programs and closing it frequently with the CnQ enabled, it was boosting up the system to 2.5GHz and going back to 1.2GHz and it was pretty stable. It gets unstable when i over it to 2.6GHz. My only fear is if it'll shorten my processor life with this 'hi-speed CnQ' going up n' down.

Hope anyone else have the answers for the rest of questions above.

---

### Post by Gunman1982 on 2008-07-11
The thing that will shorten the life of your processor is heat, higher Hz-> more heat-> shorter life. Switching shouldn't be a problem and running on 1.2GHz most of the time is better for the cpu.

---

### Post by Titan8990 on 2008-07-11
Not when OCing...

Anything that could possibly "automatically" change settings related to voltages, RAM timings, clock speeds, etc should be turned off whenever overclocking your system.

---

### Post by [Jaguar] on 2008-07-11
Thanks for the reply.

The CPU isn't heating.. well actually IDK, is 43 C at 100% CPU Usage for around 7, 8 minutes heating? There's three fans directed to the CPU. One is the default that came with AMD's box and two are coolers that i removed from broken PSU's, One of them is sorta powerful.

The computer idle keeps around 33 C, Ambient temp. around 27 C.

---

### Post by [Jaguar] on 2008-07-11
> **Titan8990 said:**
> Not when OCing...

Anything that could possibly "automatically" change settings related to voltages, RAM timings, clock speeds, etc should be turned off whenever overclocking your system.

Thanks for the reply.

Yea, you're right.. I better disable it, better pay a lil' more dimes on the energy bill than buying a new computer

--

Please read other problems above and tell me if there is a solution available. Thanks.

---

### Post by [Jaguar] on 2008-07-11
Bump.. :]

---

### Post by [Jaguar] on 2008-07-12
Here's some shots..

**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
Missing icons, there was supposed to be the "Not Connected" icon and the orange box of Updates.


**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
Topbar sometimes get invisible

**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
Broken buttons, shows on mouse hover, the last photo I've hovered the mouse on "Computer"

**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
Not even Ubuntu Forums. This seems to be some kind of Font filtering like ClearType, that the broken driver can't work?

**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
'Sysinfo' closes when I click on 'nVidia' tab

**[COLOR="Red"]REMOVED ~ [Jaguar][/COLOR]**
Using the default "nv" driver instead of the "nvidia" driver, I'm able to use the Ubuntu normally, but without any visual effects ( i really want them ). I'm also able to enter on 'nVidia' tab of Sysinfo, but when i click on "NVIDIA Display Settings" it shows this box. Enabling this X config or something will make everything go back to the broken driver, the "nvidia".

I want at least this problem solved ASAP, the refresh rates and resolutions are fixed now, I've manually selected my monitor brand with a setup and it fixed the rates.


---

Nevermind this reply. Fixed.

---

### Post by [Jaguar] on 2008-07-12
Nevermind the post above with the pictures ( I've removed. ), Most of the problems has been solved on 8.04 Hardy update, but some keeps;

"1 - The first I noticed; I've got a LG Flatron L1550S 15'' (I use it on
office) that only goes to 1024x768 and apparently the boot screen is 1280x1024 ( it is able to show on a 17'' Monitor ( My houz' monitor ) ). Not huge problem but pretty annoying, is there any fix?

....

7 - How can i set manually the CPU affinity? the "taskset" cmd is pretty annoying and hard (For me) to use

That's all for now.

And i have a suggestion...

Can i set for every desktop, one processor? ( Like on the bottom toolbar i can change two desktops, can i set one processor for each desktop? ) ( You may think: If the window is between the desktops? Well, it may use both processors.. )

And a question..

Is there any cool racing/shooting game for Ubuntu?"

And there's some more questions...

Is there a kind of "shortcut" to 'System Monitor' like 'Ctrl Alt Del' for Taskmgr on Windows?

Why sometimes my 2nd processor keeps working at 30, 40% when the System monitor shows 0% CPU to all processes? ( I've set it to show all processes available )

---

### Post by [Jaguar] on 2008-07-12
Bump.

Apparently my MS IntelliMouse side buttons won't work on the normal windows ( not the O.S. ) but only on the Firefox. Why?

---

### Post by [Jaguar] on 2008-07-13
help!

---

### Post by unutbu on 2008-07-13
If you don't have imwheel installed, perhaps try that:
[http://ubuntuforums.org/showpost.php?p=5239784&postcount=26](http://ubuntuforums.org/showpost.php?p=5239784&postcount=26)

---

