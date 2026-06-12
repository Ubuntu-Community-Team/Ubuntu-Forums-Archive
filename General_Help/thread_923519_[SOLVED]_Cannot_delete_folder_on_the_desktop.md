---
title: "[SOLVED] Cannot delete folder on the desktop"
date: 2008-09-18
forum: General Help
---

### Post by ^^rac on 2008-09-18
Hi guys....

Copied this from a CD, when i want to delete it, i get this?

---

### Post by Infinite Indefinite on 2008-09-18
Go to Applications > Accessories > Terminal 

and then navigate to wherever the file is.

Then type "sudo rm -f Cou" and press Tab to complete the name.

Then press enter, provide the password and the file should be deleted.

---

### Post by Elfy on 2008-09-18
You need to do it with root rights, either run nautilus as root {code]gksudo nautilus[/code] and do it from there or use rm in a terminal ```
sudo rm -r ~/Desktop/Counter
```use tab to autocomplete the name

---

### Post by -Zeus- on 2008-09-18
> **Infinite Indefinite said:**
> Go to Applications > Accessories > Terminal 

and then navigate to wherever the file is.

Then type "sudo rm Cou" and press Tab to complete the name.

Then press enter, provide the password and the file should be deleted.

totally wrong.  just press alt+f2 and type "gksu nautilus", navigate to the file, and delete it like normal.  or if you want to use the terminal, run the following from a terminal: 

```
sudo rm -rf ~/Desktop/Counter\ Strike\ 2.0\ With\ Source
```

---

### Post by Titan8990 on 2008-09-18
It is a folder so he will want to use the -r flag. Be warned incorrect use can lead to a toasted system.


sudo rm -r /home/YOURUSERNAME/Desktop/Counter\ Strike\ 2.0/

---

### Post by ^^rac on 2008-09-18
> **Infinite Indefinite said:**
> Go to Applications > Accessories > Terminal 

and then navigate to wherever the file is.

Then type "sudo rm Cou" and press Tab to complete the name.

Then press enter, provide the password and the file should be deleted.

Hehehe, thanks, i knew it was gonna be something in the terminal....

But i get this? rm: cannot remove `Counter Strike 2.0 With Source/': Is a directory

---

### Post by Nxion on 2008-09-18
Is is because the file is locked either by permissions. to delete it.
```

sudo rm -rf /home/*username"/Desktop/C
```and then hit tab ***BEFORE*** you hit enter, it should finish out the directory. But you have to be careful with this because if you don't finish out the directory it will delete the whole desktop folder.

---

### Post by -Zeus- on 2008-09-18
> **Titan8990 said:**
> It is a folder so he will want to use the -r flag. Be warned incorrect use can lead to a toasted system.


sudo rm -r /home/YOURUSERNAME/Desktop/Counter\ Strike\ 2.0/

that won't work either;  not the full path.  Just use what I posted

---

### Post by Nxion on 2008-09-18
> **^^rac said:**
> Hehehe, thanks, i knew it was gonna be something in the terminal....

But i get this? rm: cannot remove `Counter Strike 2.0 With Source/': Is a directory

If you do "sudo rm -rf" that will delet the folder and all its contents. r =recursive and f = folder. Hope this helps :)

---

### Post by -Zeus- on 2008-09-18
> **^^rac said:**
> Hehehe, thanks, i knew it was gonna be something in the terminal....

But i get this? rm: cannot remove `Counter Strike 2.0 With Source/': Is a directory

Just do what exactly I said.

---

### Post by -Zeus- on 2008-09-18
> **Nxion said:**
> If you do "sudo rm -rf" that will delet the folder and all its contents. r =recursive and f = folder. Hope this helps :)

-f is for surpressing errors on nonexistant files, has nothing to do with folders.

Come on people, please!  It appears to be evident that I am the ONLY ONE with any working knowledge of BASH!!!

---

### Post by Nxion on 2008-09-18
> **-Zeus- said:**
> that won't work either;  not the full path.  Just use what I posted


Yes it will. What you did was just shorten the "/home/username" to "~/". They both work the same way.

---

### Post by Titan8990 on 2008-09-18
My command was fine other than the fact I missed part of the file name....

---

### Post by -Zeus- on 2008-09-18
> **Nxion said:**
> Yes it will. What you did was just shorten the "/home/username" to "~/". They both work the same way.

> **Nxion said:**
> sudo rm -rf /home/*username"/Desktop/C

Mind telling me what in the world '*username"' is??!

---

### Post by ^^rac on 2008-09-18
> **-Zeus- said:**
> Just do what exactly I said.

Thanks guys!

It worked:)

Awesome!

---

### Post by -Zeus- on 2008-09-18
> **Titan8990 said:**
> My command was fine other than the fact I missed part of the file name....

Dude.  miss too much of and you can blow away his whole install... that's really no excuse for sloppiness.

---

### Post by sisco311 on 2008-09-18
> **^^rac said:**
> Hi guys....

Copied this from a CD, when i want to delete it, i get this?
from a terminal:
```
sudo chown -R $USERNAME: ~/Desktop
```
then try to delete it.

---

### Post by -Zeus- on 2008-09-18
> **^^rac said:**
> Thanks guys!

It worked:)

Awesome!

Great.  Now maybe a mod should lock this thread.

---

### Post by Titan8990 on 2008-09-18
It means replace the word username with your actual username Zues. It is like a variable to be used by humans...



Edit: And no, it would have told him file/directory not found, it would not have blown away his machine...

---

### Post by Nxion on 2008-09-18
> **-Zeus- said:**
> Mind telling me what in the world '*username"' is??!


"username" is a placeholder for what ever his user name is.... It is pretty self explanatory.

---

### Post by Nxion on 2008-09-18
> **Titan8990 said:**
> It means replace the word username with your actual username Zues. It is like a variable to be used by humans...



Edit: And no, it would have told him file/directory not found, it would not have blown away his machine...


Exactly right Titan. My point exactly...

---

### Post by sisco311 on 2008-09-18
> **^^rac said:**
> Thanks guys!

It worked:)

Awesome!
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thread Tools**.

---

### Post by Nxion on 2008-09-18
> **^^rac said:**
> Thanks guys!

It worked:)

Awesome!


Glad we could be of assistance :)

---

### Post by bodhi.zazen on 2008-09-18
USE THE FORCE LUKE :twisted:

I am shocked that no one mentioned tab completion.

In a terminal :

```
sudo rm -rf ~/Des<tab>/Cou<tab>
```

Tab completion really really helps with "file\ names\ with\ spaces" and long_file_names_that_take_a_very_long_time_to_type_and_can_therefore_introduce_spellink_errors

---

### Post by Titan8990 on 2008-09-18
Bodhi, tab completion was mentioned multiple times on the first page of this thread.

---

### Post by Nxion on 2008-09-18
> **bodhi.zazen said:**
> USE THE FORCE LUKE :twisted:

I am shocked that no one mentioned tab completion.

In a terminal :

```
sudo rm -rf ~/Des<tab>/Cou<tab>
```Tab completion really really helps with "file\ names\ with\ spaces" and long_file_names_that_take_a_very_long_time_to_type_and_can_therefore_introduce_spellink_errors

It is deferentially useful, it took me a while to get used to it. I would just write out the long string and forget about tab completion :|

---

### Post by ^^rac on 2008-09-18
Hey guys!

You all are great! Cause you Ubuntu users.....

Thanks for helping me and each other!

Ubuntu FTW! :KS

---

