---
title: "[SOLVED] Can filename extensions be hidden?"
date: 2008-07-14
forum: General Help
---

### Post by dodle on 2008-07-14
I would like to configure my desktop (xfce4) and file manager (thunar) to hide filename extensions, like in Windows.  Is there a way to do that?

Thanks in advance.

---

### Post by fyo on 2008-07-14
Welcome to the wonderful world of Linux.

Linux doesn't use file extensions. It's all just part of the file name, so it doesn't make any sense to hide it ("it" not being there).

You can rename all your jpg's .jpeg or .xxx or completely remove the extension. "Linux" won't care one bit.

File types are determined using "magic numbers".

---

### Post by sayakb on 2008-07-14
Windows decides file type based on extensions, unlike Linux. The UNIX filesystem decides file types by special *magic numbers* at the beginning of the file. Hiding file extensions may be a security risk, as an executable may potentially hide itself. I'm not sure that this can be done. You may manually delete the file extensions by renaming specific files though.
> This is actually THE windows design flaw that aids a lot of exploits and viruses. 
[http://brainstorm.ubuntu.com/idea/5110/](http://brainstorm.ubuntu.com/idea/5110/)

---

### Post by dodle on 2008-07-14
Okay, I changed an .mp3 to a .jpg and it tried to open it in an image viewer.  As long as I change the extension to one that is not in use, it's just fine, or if I just delete the ext.  If there is a way to just hide them, that is what I would prefer.  If not, then I will just suffer.

---

### Post by dodle on 2008-07-14
> **LinuxIsInnovation said:**
> Hiding file extensions may be a security risk, as an executable may potentially hide itself.

Well, I guess if it's going to mess up executables I don't want to do it.  I was worried about my mom renaming files and then not being able to use them.  But, since deleting the ext. doesn't affect it, I guess I have nothing to worry about.

---

### Post by sayakb on 2008-07-14
> **dodle said:**
> Okay, I changed an .mp3 to a .jpg and it tried to open it in an image viewer.  As long as I change the extension to one that is not in use, it's just fine, or if I just delete the ext.  If there is a way to just hide them, that is what I would prefer.  If not, then I will just suffer.

After changing the .mp3 to .jpg, it should automatically open in a music player when double clicked on..

---

### Post by lisati on 2008-07-14
> **LinuxIsInnovation said:**
> Windows decides file type based on extensions, unlike Linux. 

While that is generally true, I've met MS-DOS '.COM' files that were really '.EXE' files in disguie. Windows & MS-DOS start with the extension, and then look for an EXE file header, which provide extra information to the loader (e.g. if it's a DOS program or a Windows program, sometimes which version of Windows it's for, and a bunch of other stuff as well). I've even heard of a .BAT file that could also be run as a .COM file. Unless I'm mistaken, something similar goes on with other kinds of file - I've had "MP3" files come my way which weren't, programs which believe only the extension weren't able to play them.

---

### Post by sayakb on 2008-07-14
> **lisati said:**
> While that is generally true, I've met MS-DOS '.COM' files that were really '.EXE' files in disguie. Windows & MS-DOS start with the extension, and then look for an EXE file header, which provide extra information to the loader (e.g. if it's a DOS program or a Windows program, sometimes which version of Windows it's for, and a bunch of other stuff as well). I've even heard of a .BAT file that could also be run as a .COM file. Unless I'm mistaken, something similar goes on with other kinds of file - I've had "MP3" files come my way which weren't, programs which believe only the extension weren't able to play them.

What I meant by "Windows decides file types based on extensions" is that it would recognize an mp3 with a .jpg extension as a JPEG Image. It will show the icon of a jpeg image and open it with the application associated with jpeg images. That doesn't mean you can't open it on their respective applications (The **open with...** thingy ;))
Plus, a COM file may be similar to an EXE, but is totally different from a BAT (which is usually a sequence of commands, but not an executable)
Sorry if I am wrong.. it's been a long time since I have abandoned windows now.. :)
[http://en.wikipedia.org/wiki/COM_file](http://en.wikipedia.org/wiki/COM_file)
[http://en.wikipedia.org/wiki/EXE](http://en.wikipedia.org/wiki/EXE)
[http://en.wikipedia.org/wiki/.bat](http://en.wikipedia.org/wiki/.bat)

---

### Post by dodle on 2008-07-14
Maybe it has something to do with the xfce4 desktop, but when I changed the filename extension to from .mp3 to .jpg, then double-clicked it, gthumb was executed and attempted to open the file.  Any other extensions I used, like ".xxx" or ".blah" and the file opened in the music player.

---

### Post by sayakb on 2008-07-14
Err.. Maybe not.. This happens when you enter another extension associated with some other application. Happens on gnome also. Just the difference from Windows is that renaming it to .xxx or anything that isn't recognized doesn't make the file lose it's default program association (In Windows, you have to either Open With... or change to a valid extension in such case)

---

### Post by jocko on 2008-07-14
A very good reason (in windows) to make sure you **NEVER** **EVER** hide file extensions for any file is that there are viruses that mask themself by having a name like filename.mp3.exe (and probably any other "harmless" extension followed by .exe, .com or .bat). By some weird reason the guys at microsoft aren't very consistent, so a file get's it's icon from whatever is after the first dot in the file name, but get's it's associations from whatever is after the last dot...
So an .mp3.exe file may look like a harmless mp3, but when you double click it, you may execute a nasty virus...
But none of this would happen in linux...

I have noticed a few times that when I have tried starting a movie file by double clicking it, I've got messages like "The file you try to open indicate that it is of the type mpeg/video, but it's extension is .avi..." or something similar, and in those cases the only ways to start such a file is to either rename it to the "correct" extension or to open it with a media player directly instead of double-clicking the file.
So saying linux doesn't look at file extensions is wrong. It does, or at least there is some security feature in gnome/nautilus/ubuntu/whatever that looks at extensions...

---

