---
title: "Split rar files won't extract"
date: 2008-11-10
forum: General Help
---

### Post by Rubicon421 on 2008-11-10
I know there are several posts on this already but I have not found a working solution in any of them. I can't get split rar archives to extract with archive manager, Xarchive, 7-zip (linux or windows w/ wine), win rar (wine) or zipgenius(wine). 
Archive manager and Xarchive say they are unsupported and any windows program I have tried in wine just starts to extract and gets an error when it gets to the end of the first part.
What do you use?

---

### Post by ju2wheels on 2008-11-10
Ubuntu's built in file roller handles multi-file rar's quite fine. Remember that when unraring the files, you only need to unrar the file with the .rar extension and the rest of the files with the numerical extensions will automatically be unrared. You must also have all those files in the same directory for it to work.

If you want to use the command line instead of the built in file roller then you will have to install rar and unrar:
```

sudo apt-get install rar unrar

```

Edit: In order to create a rar archive with the file roller/archive manager you need to have rar installed, so it may be required to install unrar if you want to extract rar's with it as well, but Im not sure as I already had both of them installed and dont recall if I installed it manually.

---

### Post by Rubicon421 on 2008-11-10
O.K. Sorry about being such a noob but I've never used any form of Linux expect for the last few days. I have no idea how to use that code and I can't find the file roller program that you are talking about.

---

### Post by ju2wheels on 2008-11-10
Open Applications->Accessories->Terminal and type the above line into the window. It will isntall rar and unrar after it asks you for your password.

The file roller is the application that shows up when you right click on any file or folder and select "create archive". The archive manager shows up when you double (left) click on an archive, in this case your rar file.

---

### Post by Rubicon421 on 2008-11-10
Thanks, I've got a few to work but still having trouble with one particular set or archives. Maybe it's just corrupt.

---

### Post by martysweeney on 2009-04-29
> **ju2wheels said:**
> Open Applications->Accessories->Terminal and type the above line into the window. It will isntall rar and unrar after it asks you for your password.

The file roller is the application that shows up when you right click on any file or folder and select "create archive". The archive manager shows up when you double (left) click on an archive, in this case your rar file.


this was great, it helped me load thanks ju2wheels.. :)

---

### Post by Shampyon on 2009-07-18
I've had troubles with split archives occasionally when using Graphical User Interfaces for *unrar*.

If you have similar trouble, try this:-
Open the terminal and navigate to the directory containing the archive parts.
```
cd /path/to/file/
```
For example
```
cd ~/Downloads/
```
The tilde (**~**) is a command line shortcut for [FONT="Courier New"]**/home/USERNAME/**[/FONT]
Once you've navigated to the directory, you'll want to copy the filename of the first archive part, eg: **[FONT="Courier New"]File.name.creator.date.etc-etc.part1.rar[/FONT]**
If you've used Windows, you'll know how to do this the GUI way. Keep the Terminal window open though - you'll still need it. Once you've copied the first archive part's name, enter the following into the terminal:
```
unrar x File.name.creator.date.etc-etc.part1.rar
```
Unless you've changes the settings, you should have to use *SHIFT+CTRL+V* to paste the copied file name into the terminal. Now just press *Enter*. It may ask you for a password - be aware that when you type it in, you won't see any characters (not even asterisks *****) appear. This is a security feature, to make sure no-one can just look at your screen and steal your passwords.

I know, all that command-line stuff look scary. Don't worry. You do it a couple of times and it'll become easy as pie :)

---

### Post by castawaybcn on 2009-07-18
a very simple addition to what Shampyon mentioned. If you find typing a long name in the command line is a bore (which it is) try the following:
After you are in the directory, which you did by:
```
cd ~/Downloads/
```
start typing the command and just the beginning of the file's name, that is (as with the previous example):
```
unrar x Fi
```
then press "tab" and the command line will fill it up for you (or provide options in case there are different files which start the same)

I also found very helpful installing nautilus-open-terminal, which adds an option in the right-mouse-button menu to open a terminal with the path of the current folder. To install just type in a terminal:
```
sudo apt-get install nautilus-open-terminal 
```
or if you prefer the graphical way, go to System>Administration>Synaptic Package Manager and look for nautilus-open-terminal 

Hope it helped

---

### Post by Shampyon on 2009-07-18
Cool, I didn't know that tab trick. Thanks!

---

### Post by skullmunky on 2009-07-18
Another sometimes-useful unrar trick - if you have a lot of parts and one is corrupt, unrar will not extract anything.  But sometimes when you have a rar file of a directory or other things like that, it's useful to get something out of at least the parts before the broken section.  You can do that with the "-kb" for "keep broken" flag:

```

unrar x -kb myfile.rar.01

```

---

### Post by xxilus on 2010-05-22
Am I the only one getting this when they try to install rar?

```
apt-get install rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

```

---

### Post by pr0t3g3 on 2010-05-22
> **xxilus said:**
> Am I the only one getting this when they try to install rar?

```
apt-get install rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

```
wrong command its not just install rar its:

sudo apt-get install rar unrar

rar AND unrar ^_^ if that doesnt work I can't help you ... I had the same problem with my playstation diablo 1 .iso files so thanks for your post credit due to the other posters of course ;P

---

### Post by jamesisin on 2010-05-22
For what it's worth, I find 7Zip works best.  I wrote an article for installing and using it here:

[http://www.soundunreason.com/InkWell/?p=450](http://www.soundunreason.com/InkWell/?p=450)

---

