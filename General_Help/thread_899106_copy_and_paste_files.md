---
title: "copy and paste files"
date: 2008-08-24
forum: General Help
---

### Post by bossyman15 on 2008-08-24
how do i copy and paste files?

i need to copy files off my flash drive but i can't paste the file or move them to a folder in xubuntu.

how do i do this?

---

### Post by rossjman1 on 2008-08-24
The same way you would in Windows. Highlight the file and right click and copy/cut and paste in the folder you want to copy/move the file to.

---

### Post by LateNiteTV on 2008-08-24
```
cp /path/to/files /path/to/destination
```

---

### Post by etnlIcarus on 2008-08-24
> **bossyman15 said:**
> how do i copy and paste files?

i need to copy files off my flash drive but i can't paste the file or move them to a folder in xubuntu.

how do i do this?

Firstly, we need more information.

When you open the file manager, does the flash drive appear in the shortcuts pane on the left-hand side?

Can you view the contents of the flash drive when you click on the shortcut?

What happens when you try to right-click icon>copy and right-click second window>paste?

---

### Post by bossyman15 on 2008-08-24
> **etnlIcarus said:**
> Firstly, we need more information.

When you open the file manager, does the flash drive appear in the shortcuts pane on the left-hand side?

Can you view the contents of the flash drive when you click on the shortcut?

What happens when you try to right-click icon>copy and right-click second window>paste?

well when i highlight the items i want to copy i right click ---> copy then i go to the folder i want to paste, i right click but the paste option is greyed out. ctrl - V doesn't work too.

---

### Post by etnlIcarus on 2008-08-24
Possible issue: do you close one window before opening the next?

*nix desktops don't have a clipboard in the traditional sense.

If you open two windows and have them side-by-side, you should be able to copy and paste. Hell, you should be able to drag-and-drop.

Also, a way around this issue is to add a clipboard manager to your xfce panel:

[img]http://img413.imageshack.us/img413/1289/screenshotadditemstotheee4.png[/img]

Edit: Also another possible issue is you're trying to copy the files to a folder you don't have write permissions for. Are you trying to copy them to somewhere in your /home/<username>/ directory or are you trying to paste them somewhere else?

A good place to put the pasted files would be /home/<username>/Documents/

A bad place would be / or /usr/.

---

### Post by bossyman15 on 2008-08-24
i just found out something

the folder i was trying to paste to was htdoc for apache but the folder like /home i can paste. 

in httdoc i checked properties and i see in permissions that everything is greyed out and i can't change anything. and that the owner is nobody (nobody)

---

### Post by etnlIcarus on 2008-08-24
You've got several options here. The best of which is to become familiar with sudoing.
Eg.

$ sudo cp -r /media/flashdrive/files/ /wherever/httdoc/

Depending on where the directory is, you might also want to consider changing the owner of the folder.

$ sudo chown -hR <username> /wherever/httdoc/

If the directory is in a system-wide directory tree which other users may also need access to, though, chmod is a better option. if the folder is in the /home/<username> tree, feel free to change it's ownership permissions, though.

A real example of chmod (I'm a little rusty myself):

```
icaria@xubuntu-box:~$ mkdir test
icaria@xubuntu-box:~$ cd test
icaria@xubuntu-box:~/test$ nano
icaria@xubuntu-box:~/test$ ls -l
total 4
-rw-r--r-- 1 icaria icaria 5 2008-08-24 16:48 test.txt
icaria@xubuntu-box:~/test$ chmod -R +wxrwxrwxr test.txt 
icaria@xubuntu-box:~/test$ ls -l
total 4
-rwxr-xr-x 1 icaria icaria 5 2008-08-24 16:48 test.txt

```

I created a text.txt document in a test directory.
When I first listed it, it showed rather limited set of permissions (-rw-r--r--).
After I chmoded the file, the permissions were more extensive (-rwxr-xr-x)
Wiki can probably explain it better than I can: [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

Your other option is to open nautilus up as root:

$ sudo nautilus --no-desktop

Then you can go to the relevant directory and manually change the permissions and ownership with a GUI. It's generally best to simply change permissions, rather than ownership.

---

### Post by bossyman15 on 2008-08-24
thanks! the command
$ sudo chown -hR <username> /wherever/httdoc/
worked for me! 
now i can paste files in there.

thank you!

i'm learning a bit now.

---

### Post by bodhi.zazen on 2008-08-24
Well, that was probably not the best advice.

You should not change the ownership and permissions of system files unless you know what you are doing.

Use sudo , or for grahpical applications gksu.

So, 

```
sudo cp file /wherever/httdoc/
```

But you probably then want to change permissions of the file

ls -l /wherever/httdoc/

then once you see the wonership / permissions

sudo chown user.group /wherever/httdoc/file
sudo chmod xxx /wherever/httdoc/file

For graphical applications,

```
gksu nautilus
```

References:

[uhelp]community/RootSudo[/uhelp]

[uhelp]community/FilePermissions[/uhelp]

_Note_: The problem with changing ownership and permissions of system directories is that you can compromise system security, which on a web server is not good.

---

