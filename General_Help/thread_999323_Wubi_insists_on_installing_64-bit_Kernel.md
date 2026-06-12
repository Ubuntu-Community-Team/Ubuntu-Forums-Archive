---
title: "Wubi insists on installing 64-bit Kernel?"
date: 2008-12-01
forum: General Help
---

### Post by jtanunleashed on 2008-12-01
Hi, I've attempted to install Ubuntu and Wubi and had a few problems.  

Firstly the current problem:
I've tried to install Wubi, which all went successful until the restart.  On loaded, I got this error message:
[IMG]http://farm4.static.flickr.com/3144/3075944958_9eecd55882.jpg[/IMG] ([http://flickr.com/photos/8534030@N06/3075944958/]("http://flickr.com/photos/8534030@N06/3075944958/"))
As you can see, the problem is Wubi has attempted to install a kernel that requires an x86-64 CPU, but the actual installed CPU is an i686.

Now, I've attempted to install Wubi in several ways; storing the ISO on a CD, in the same folder, and leaving Wubi to choose an ISO to download itself.  I also used the Run argument "G:/wubi.exe --32bit" which resulted in the screenshot given.

**Is there any way I can upgrade the kernel from within Windows so that I can solve this problem?  Or, if thats not possible, can you explain how to properly uninstall/reinstall to avoid this kernel problem again?  Thanks for your help...**

Before this, I attempted to install Ubuntu the proper way, by downloading the ISO, CD5SUM checking and installing fully.  But Grub 1.5 returned error 1.5 and I had to *fixmbr*; *fixboot* to return to Windows.

The info you might need is that I'm trying to dualboot Windows XP (already installed on the C:/ drive) with Ubuntu (which I'd like to install on the external G:/ drive for space reasons).

Thanks :)

---

### Post by abn91c on 2008-12-01
download a 32bit ubuntu live cd, browse in windows explorer then click on the wubi icon to install, you can select install inside windows option when the dialog box appears in windows when you insert the CD-ROM aslo.

---

### Post by jtanunleashed on 2008-12-01
> **abn91c said:**
> download a 32bit ubuntu live cd, browse in windows explorer then click on the wubi icon to install, you can select install inside windows option when the dialog box appears in windows when you insert the CD-ROM aslo.

Thanks for the advice but I've already tried it, and it still gives the same result.

---

### Post by abn91c on 2008-12-01
Not sure whats happening but search the forums for fat vs ntfs formats to see if thats the problem. I dual boot kubuntu/windows Xp on a dell dimension 2400 original dell setup, my drive is ntfs and it wokrs fine, actually kubuntu is a lot faster than XP

---

### Post by magmon on 2008-12-02
x86 is 32 bit. I have no idea why computer people need to make confusing multiple names for everything, but try the install and see what happens. As to the error, that is most certainly odd...

---

### Post by ago on 2008-12-02
I cannot see the screenshot can you describe what is in there?

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> I cannot see the screenshot can you describe what is in there?

hmm...THAT'S strange!!! why can't u see the screenshot? i can see it just fine... :guitar:

EDIT: ok, for ago's sake, i'll describe what's in the screenshot...

There's a computer screen, on which it says: 

```
Booting 'Ubuntu 8.04, kernel 2.6.24-17-generic'

Filesystem type is Fat, partition type 0x0C
The current working directory is(i.e., the relevant path) is /ubuntu/

[Linux bzImage, setup=0xZa00, size=8x1cdf98]
[Linux initrd @ 0x3ef6b000, 0x75759c bytes]

This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```

Hope this helps! :)

---

### Post by magmon on 2008-12-02
Lol ago, the screen says:
booting ubuntu8.04, kernel 2.6.24-17-generic

filesystem type is fat, partition 0x0c
The current working directory (i.e.. the relative path) is /ubunbu/....
Blah blah blah..
[COLOR="DeepSkyBlue"]this kernal requires a x86-64 CPU, but only detected a i686 cpu[/COLOR]
Unable to boot-Please use a kernel appropriate to your CPU

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Lol ago, the screen says:
booting ubuntu8.04, kernel 2.6.24-17-generic

filesystem type is fat, partition 0x0c
The current working directory (i.e.. the relative path) is /ubunbu/....
Blah blah blah..
[COLOR="DeepSkyBlue"]this kernal requires a x86-64 CPU, but only detected a i686 cpu[/COLOR]
Unable to boot-Please use a kernel appropriate to your CPU

uhh...Magmom...i just copied it for him in my above post!!! ^^

why would u write it as well? 

:guitar:

---

### Post by jtanunleashed on 2008-12-02
> **ago said:**
> I cannot see the screenshot can you describe what is in there?

> **Jammanuser said:**
> hmm...THAT'S strange!!! why can't u see the screenshot? i can see it just fine... :guitar:

EDIT: ok, for ago's sake, i'll describe what's in the screenshot...

There's a computer screen, on which it says: 

```
Booting 'Ubuntu 8.04, kernel 2.6.24-17-generic'

Filesystem type is Fat, partition type 0x0C
The current working directory is(i.e., the relevant path) is /ubuntu/

[Linux bzImage, setup=0xZa00, size=8x1cdf98]
[Linux initrd @ 0x3ef6b000, 0x75759c bytes]

This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```

Hope this helps! :)

I also posted the URL of the picture, where I did transcribe the error for those who couldn't read it.  Seems you probably need to be a bit more lenient with your browser's picture display settings, or move to a browser that does display a normal web view.

Thanks for the help everyone, I assumed from the **-64** part that this was a 64-bit compatible kernel, and that the installed CPU is 32-bit.

---

### Post by jtanunleashed on 2008-12-02
Nothing seems to be working, I even tried purposefully using a 64-bit version of Ubuntu, but no matter what I do, whatever version I get, I always end up with that same error message.  For some reason it won't install Ubuntu 8.10 and it won't use a version compatible with my i686 CPU.  I'm all out of ideas :s

---

### Post by ago on 2008-12-03
Uninstall wubi. Remove any ISO you might have around, including C:\, Desktop and the folder containing wubi.exe. Then put the 32bit ISO and wubi.exe in the same folder and run wubi.exe.

---

### Post by keiftek on 2011-05-01
Ihave recieved the same message, when downloading Ubutu 11. I have upgraded windows to windows 7 ultimate. Older computer. What is the appropriate version of ubuntu that will work? Fairly new to using computer--be gentle.

---

### Post by oldos2er on 2011-05-01
keiftek, please start a new thread; no one's likely to see your question here.

---

