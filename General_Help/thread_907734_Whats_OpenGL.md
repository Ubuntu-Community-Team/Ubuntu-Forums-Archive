---
title: "Whats OpenGL"
date: 2008-09-01
forum: General Help
---

### Post by VengefulIce on 2008-09-01
Hi all

ok so i am completely new to ubuntu
I installed wine, and installed WC3 from there.  I tried running it, and it doesn't run too smoothly.  After reading some forums, i saw that people were saying that OpenGL helps, but i have no idea where to find OpenGL or where to add it or whatever!!

Thanks in advance

---

### Post by Habbit on 2008-09-01
Hi VengefulIce

First of all, welcome to Ubuntu, and, I presume, to the Light Side of the Force (i.e. the Linux world). OpenGL is a graphics library providing programs with access to the 3D graphics acceleration capabilities of your graphics card, and is used very frequently in games. Windows programs sometimes use DirectX, which is an equivalent Windows library, but Wine uses OpenGL under the hoods to emulate DirectX functions and achieve equivalent effects.

In order to use OpenGL, the driver for your graphics card has to support it. What graphics card have you got? Is direct rendering enabled? For the first question, look for a line like "VGA compatible controller" at the output of "lspci"; for the last question, look for the "direct rendering" line in the output of the "glxinfo" command.

---

### Post by Crushyerbones on 2008-09-01
If that was too confusing, just think of it as DirectX for Linux :)

Although DirectX is only usable on Windows operating systems, OpenGL is free and used by games like the "Quake"s, Homeworld, etc.

---

### Post by VengefulIce on 2008-09-01
ok i have a NVIDIA GeForce FX5200
and yes direct rendering is enabled

---

### Post by rossjman1 on 2008-09-01
Then go into the game's options and use OpenGL instead of software rendering.

---

### Post by VengefulIce on 2008-09-01
do you mean ingame or what?
thanks

---

### Post by Habbit on 2008-09-01
Yeah, that usually means ingame.

BTW, even if your current graphics driver "supports" OpenGL, note that Ubuntu ships by default with open source drivers enabled. However, nVidia and ATI release binary drivers (i.e. without full sources) that can sometimes* provide a better result than the open source drivers. If you want to try the binary nVidia drivers for your card, go to "System->Administration->Hardware drivers" and select them from the list of available 3rd party drivers.

*with my ATI X850 XT the binary drivers provide full 3D acceleration and even compositing (which causes sporadic hangups with the OSS drivers), but overheat the card and make the (rather noisy) fan run at full blast most of the time, so I use the OSS drivers only.

---

### Post by VengefulIce on 2008-09-01
ok well if its ingame then...  warcraft 3 probably doesnt support it..  Is there any other way to make things run smoother?

---

### Post by Habbit on 2008-09-01
Apart from the binary drivers? Well, have you checked it's not a W3-specific issue? I mean, do other 3D games run smoothly? In my case, I can run Steam/Counter-Strike but W3 is too much for my video card under the default drivers.

---

### Post by VengefulIce on 2008-09-01
i just read something that adding -opengl after "wine Frozen Throne.exe" would have it run in opengl instead of direct3d, but when i try that, i get the error "wine: could not load L"C:\\windows\\system32\\Frozen.exe" Module not found"

ugh!!

---

### Post by Habbit on 2008-09-01
Since the file name contains spaces, you need to quote it: wine "Frozen Throne.exe" -opengl. Otherwise, wine gets "Frozen" "Throne.exe" "-opengl" as arguments, and tries to run a program called Frozen (.exe) with "Throne.exe" and "-opengl" as arguments. Slightly confusing, yeah, but you just need to remember that spaces are separators in the command line and you have to either put them in quoted strings or escape them with a \ character.

---

### Post by VengefulIce on 2008-09-01
it always says module not found..

---

### Post by Habbit on 2008-09-01
Are you running the command with the full path or in the correct directory? If you installed W3 in C:\Games\Warcraft III, you need to put:

wine C:\\Games\\Warcraft\ III\\Frozen\ Throne.exe -opengl

Or run the unqualified command (i.e. without the path) from within the W3 directory. Usually your "C:" Wine drive is at /home/yourusername/.wine/drive_c, so you would do:

cd ~/.wine/drive_c/Games/Warcraft\ III
wine Frozen\ Throne.exe -opengl

---

### Post by VengefulIce on 2008-09-01
ok YES that was the problem
THANK YOU SO MUCH!!

oh one more question, how do you run terminal in the current directory?

---

### Post by Habbit on 2008-09-02
> **VengefulIce said:**
> oh one more question, how do you run terminal in the current directory?

Install the nautilus-open-terminal package ("sudo apt-get install nautilus-open-terminal") and a "Open in terminal" option will appear in the contextual menu of folders within Nautilus.

---

### Post by VengefulIce on 2008-09-02
ok so i installed nautilus, but i dont see the open in terminal option..

ok nevermind i found it

thanks so much

---

### Post by Uchiha_madara on 2008-09-03
> **VengefulIce said:**
> Hi all

ok so i am completely new to ubuntu
I installed wine, and installed WC3 from there.  I tried running it, and it doesn't run too smoothly.  After reading some forums, i saw that people were saying that OpenGL helps, but i have no idea where to find OpenGL or where to add it or whatever!!

Thanks in advance

OpenGl is Like DirectX that you need it to increase the Graphics that especially good for 3D games ..

---

### Post by VengefulIce on 2008-09-03
is there any way to set opengl as the default?

---

### Post by kavithabangera on 2008-09-04
can anyone please tell me drawbacks of sdl? i m new to sdl and supposed to findout alternative of sdl?

---

### Post by Dougie187 on 2008-09-04
> **VengefulIce said:**
> is there any way to set opengl as the default?

You can add the opengl launcher flag, to a launcher for the application on your desktop, and then just double click it and it should work.

AFAIK, there is also a registry key you are supposed to add for opengl support in WC3.

This should give you some more information on how to run it successfully.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

---

### Post by Zugzwang on 2008-09-04
> **kavithabangera said:**
> can anyone please tell me drawbacks of sdl? i m new to sdl and supposed to findout alternative of sdl?

No thread hijacking, please! The question is already answered in the thread of your post in the programming talk forum.

---

