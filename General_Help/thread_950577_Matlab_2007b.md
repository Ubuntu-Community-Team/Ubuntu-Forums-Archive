---
title: "Matlab 2007b"
date: 2008-10-17
forum: General Help
---

### Post by Jacob Collstrup on 2008-10-17
Heya,

I'm trying to get Matlab 2007b (unix version) to work the way its supposed to...

I got a license file from a teacher here at the university and made the license.dat out of it, according to the install instructions.

I then install matlab using the options I want (full install). After this I found that the graphical user interface did not work, all windows and toolbars was invisible, however I found a solution to that. I add the line 'export AWT_TOOLKIT=MToolkit' as the first uncommented line in the /matlab/bin/matlab-file.

However, the toolboxes doesn't work. I do a full install and Matlab should have an 'image toolbox' or something like that. I carefully make sure that ALL toolboxes called something with 'image' is installed. However when I type 'help imshow' in the command space of matlab I just get an error message saying that there is no such command as 'imshow'. But as I can understand from my teachers it should be installed.

I tried writing 'help chi2inv' and 'help tinv' as those should be functions as matlab already have integrated. However I get the same error message. I take care to run the file 'lmstart' in the terminal before I run my modified matlab-file in the terminal.

Jacob

---

### Post by Jacob Collstrup on 2008-10-20
Could it be that I'm not logged in as root or sudo, when I install?

If so, how do I do that?

Jacob

---

### Post by Claus7 on 2008-11-25
Hello,

it is a month or so, yet from your description, if you haven't found it already, I think that this is a solution to your problem:
[http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab](http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab)

Regards!

---

### Post by Jacob Collstrup on 2008-11-25
> **Claus7 said:**
> Hello,

it is a month or so, yet from your description, if you haven't found it already, I think that this is a solution to your problem:
[http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab](http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab)

Regards!

I got it to work so to speak. I copied a working toolbox library from a windows install to my installation. That created an error message inside matlab, however a temporary solution was offered in the error message. It was about the cache or something. I typed a new command I got from the matlab support and it updated the cache, so now all toolboxes work.

I just have an even more peculiar 'problem' now. when I make scripts I press [F5] to save and run...and after that I have to right click in the script editor, and choose one of the splitscreens and then set it back. Wierd...

Jacob

---

