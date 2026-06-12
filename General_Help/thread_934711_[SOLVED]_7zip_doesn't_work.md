---
title: "[SOLVED] 7zip doesn't work"
date: 2008-09-30
forum: General Help
---

### Post by masterofthemelee on 2008-09-30
Installed 7zip, Ubuntu still won't extract.

Don't know how else to explain problem.

---

### Post by davidryder on 2008-09-30
Ubuntu won't extract what?

---

### Post by karlr42 on 2008-09-30
Have a look [here](http://ubuntuforums.org/showthread.php?t=407315). How did you install 7zip? What are the options when you right click a zipped file?

---

### Post by masterofthemelee on 2008-09-30
I already installed both programs, "right click -> extract here" does nothing.  Says it can't open as archive.

---

### Post by karlr42 on 2008-09-30
What filetype are you trying to open?

---

### Post by masterofthemelee on 2008-09-30
file.7z

---

### Post by karlr42 on 2008-09-30
Correct me if I'm wrong, but the "Extract Here" option is the default Ubuntu archive manager(file-roller?). Is there not an option called 7Zip in the menu, so rightclick->7Zip->Extract here ?

---

### Post by masterofthemelee on 2008-09-30
I don't know if there is for you, but there isn't for me.

---

### Post by karlr42 on 2008-09-30
Right, disregard my last post. I just installed 7zip myself to have a look. The only thing I can think of is that the file is not a 7z file, it is merely named that way. Open a terminal and type "file file.7z" which tells you what type of file it is. I get this, for example: ```
 $ file error.wav.7z 
error.wav.7z: 7-zip archive data, version 0.2

```

---

### Post by davidryder on 2008-09-30
I haven't put any effort into it but running 7zip from Nautilus hasn't worked for me either. Does it only handle .7z files?

---

### Post by karlr42 on 2008-09-30
Worked fine for me on a .tar

---

### Post by masterofthemelee on 2008-09-30
Um, it says "permission denied".

---

### Post by masterofthemelee on 2008-09-30
Wait, nevermind, I reread your instructions a third time and realized I wasn't typing "file".

It says "data" and nothing more, though.

---

### Post by karlr42 on 2008-09-30
Then it's most likely that the file isn't a 7z file. Where did you get it?

---

### Post by masterofthemelee on 2008-09-30
To be honest, I haven't the slightest idea what it is.  I just found it in the folder I download everything into a half hour ago.

Its called "Pony_LUV.7z" and its in a folder called "Nds" which I suppose means it could be Nintendo DS homebrew.

---

### Post by karlr42 on 2008-09-30
ROMS often come in 7z archives, alright, though this sounds like junk to me. Someone probably made a text file, renamed it as .7z, and tried to pass it off as a ROM.

---

### Post by karlr42 on 2008-09-30
```

$ gedit file
$ mv file file.7z

```
[IMG]http://i523.photobucket.com/albums/w351/karlr42/fake.jpg[/IMG]

See? It's easily done, unfortunately.

---

### Post by masterofthemelee on 2008-09-30
Well it took a few minutes but I found another 7zip file, and it extracts fine.

False alarm, I guess.

---

### Post by karlr42 on 2008-09-30
Good, glad to hear it.

---

### Post by Rig'dzin Dorje on 2010-10-04
[FONT=Times New Roman][SIZE=4]I have tried installing 7zip from the Software Centre, and also downloading p7zip direct from the 7zip website. Both said they had installed OK, but they do not appear in the Applications menu, nor do 7zip options appear in the right-click menu. So I installed the Windows version under Wine, which works fine but unfortunately does not affect the right-click menu either.[/SIZE][/FONT]

---

### Post by gandaran on 2010-10-04
> **Rig'dzin Dorje said:**
> [FONT=Times New Roman][SIZE=4]I have tried installing 7zip from the Software Centre, and also downloading p7zip direct from the 7zip website. Both said they had installed OK, but they do not appear in the Applications menu, nor do 7zip options appear in the right-click menu. So I installed the Windows version under Wine, which works fine but unfortunately does not affect the right-click menu either.[/SIZE][/FONT]
p7zip doesn't appear on any menu, just right click the file and choose extract here for extracting or compress then choose the 7z format to compress the file to p7zip, it's very simple to use!
check if you installed the p7zip-full package.

---

