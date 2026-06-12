---
title: "[SOLVED] How can I save text files in Window format?"
date: 2008-11-27
forum: General Help
---

### Post by apo00 on 2008-11-27
In Ubuntu, how can I save a text file (*.txt) in the same format with Windows?
I know text files in Linux and Windows are different and I can use some software in Windows to open Linux text files. But my problem is my Nokia phone, it can't read some of Linux text files while it can read every Windows text files.
I use both Windows and Ubuntu and I don't want to switch to Windows every time I want to transfer some text to my phone.

---

### Post by DirtDawg on 2008-11-27
Two possible options I can think of, neither of which I've tried. 

First, after you are finished editing your text file in whatever editor you are most comfortable with, open your file with vim or gvim. Once it's opened, enter these commands:
```
:set fileformat=dos
:w
```
The first changes the file format to Windows, the second is the 'write' command, which is the same as 'save' in most editors (gvim will have a 'save' button). You may need to press the ESC key first to ensure you are in command mode rather than edit mode.

The second is to install Wine, a Windows emulator:
```
sudo apt-get install wine
```
In your Applications menu, there will be a Wine sub-menu (I think. I'm writing this on a Windows machine). In the sub-menu, there should be an option to use Notepad. Maybe if you save using notepad, it will be in Windows format. 

Like I said, I haven't tried either. Hope one of them works.

---

### Post by mc4man on 2008-11-27
For file's that will open directly in notepad, wordpad, ect. I'd just give your text files an .txt extension.

---

### Post by iclebyte on 2008-11-27
Traditionally there were 2 programs called unix2dos and dos2unix, however I don't know which ubuntu package they are in.

I found this though [http://ubuntuforums.org/showthread.php?t=33886](http://ubuntuforums.org/showthread.php?t=33886)
it says there is a program called 'flip' which will do the same for you - and it's in the package repositry

```
apt-get install flip
```


*edit*
Apparently dos2unix and unix2dos are in the package 'sysutils'. ```
sudo apt-get install sysutils
```

---

### Post by snova on 2008-11-27
Most editors I know of are good enough to work with both types. They should have an option to save in a different kind.

Oh, and don't forget the .txt extension. Linux doesn't care, but Windows will.

---

### Post by dagnabit dang doohickey on 2008-11-27
Unix to Windows line ending conversion:
```
sed 's/$/\r/' < *input-file* > *output-file*
```

Windows to Unix line ending conversion:
```
tr -d '\r' < *input-file* > *output-file*
```

---

### Post by apo00 on 2008-11-30
Thanks for all your helps.
I've tried all and here are results:
1) Use vim or gvim
:set fileformat=dos
* It works fine.
2) Use Wine
* It doesn't work. The file is still in Unix format.
3) Use flip
flip -bm input-file
* It works fine.
4) Use stream editor
sed 's/$/\r/' < input-file > output-file
* It works fine.

For me, I see the first one is the most convenient way. Actually gvim has an option in the pop-down menu, I don't need to type the command.

---

