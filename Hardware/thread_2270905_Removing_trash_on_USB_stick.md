---
title: "Removing trash on USB stick"
date: 2015-03-26
forum: Hardware
---

### Post by Constantinopolitan on 2015-03-26
Dear all,

I have recently purchased a new computer, installed kubuntu and am now transferring all files from my old computer via USB disk. A painstaking process because my 1 TB external hard disk failed, and I now transfer some files to a 32 GB stick, from there to the new computer, then delete them and restart the process. 
After a while I found that deleting does not work properly, the USB stick creates a hidden folder called .Trash-1000/files.
I opened the konsole and asked to delete the .Trash-1000; here is the dialogue that ensued:

```
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT/.Trash-1000/files$ sudo rm -r .Trash-1000
[sudo] password for constantinopolitana: 
rm: cannot remove '.Trash-1000': No such file or directory
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT/.Trash-1000/files$ sudo rm - .Trash-1000/files
rm: cannot remove '-': No such file or directory
rm: cannot remove '.Trash-1000/files': No such file or directory
```

Could anybody help?

When I open the hidden files I get access to .Trash-1000, but when I select all files and then simply press the delete button, nothing happens. 

I also donwloaded a programme called trash-empty.1.gz, but there is no indication where I should install it, and when I try to open it, only a text file appears.

I'd appreciate very much any helpful hint you might give!

Best regards,

Eva

---

### Post by Ko_Char on 2015-03-26
cd to the /media/constantinopolitana/LINUX MINT/

not 
/media/constantinopolitana/LINUX MINT/.Trash-1000/files

(if there is a space between LINUX MINT, you need a back slash " \ " before the space. 
Type a few characters and press "Tab" for autocompletion)

---

### Post by Constantinopolitan on 2015-03-26
Dear Ko-Char,

it didn't really help. Now the system finds another excuse for not deleting:
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT$ rm -r.Trash-1000
rm: invalid option -- '.'
Try 'rm --help' for more information.
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT$ rm .Trash-1000
rm: cannot remove '.Trash-1000': Is a directory
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT$

I know that Trash-1000 is a directory! But I still want it removed...or at least emptied.

I also tried to empty trash on my old computer (Linux Mint). There it says that when I eject the USB automatically the system asks if I want to remove trash - but no, it doesn't ask! It simply ejects. So the trash keeps accumulating. Very frustrating.

Thanks for any more tips!

Eva

---

### Post by robsoles on 2015-03-26
put a space between the '-r' and the .Trash-1000 parts.

post the next error message if there is one.

---

### Post by Constantinopolitan on 2015-03-26
Sorry...now simply NOTHING happened :-(

constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT$ rm -r.Trash-1000
rm: invalid option -- '.'
Try 'rm --help' for more information.
constantinopolitana@Constantinopolitana:/media/constantinopolitana/LINUX MINT$ rm -r .Trash-1000

---

### Post by robsoles on 2015-03-26
What you have posted doesn't make me think you have put the space where you need to yet;

```
rm -r .Trash-1000
```

---

### Post by Constantinopolitan on 2015-03-26
That's it! Thanks a lot.
USB Stick is empty now :-)

---

### Post by The Cog on 2015-03-26
In the GUI, shift-delete should properly delete files instead of just moving them to a trash folder.

---

