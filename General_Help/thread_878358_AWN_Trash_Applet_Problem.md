---
title: "AWN Trash Applet Problem"
date: 2008-08-02
forum: General Help
---

### Post by alsamman on 2008-08-02
When I right click and click Empty Wastebasket I always get this coming up
[[IMG]http://img156.imageshack.us/img156/7425/trashqj5.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=trashqj5.jpg)

But the thing is, I don't have 20 files in my trash bin and this doesn't go away (I've left it on for a while), I always have to click cancel. So any ideas on how I could fix this?

---

### Post by sayakb on 2008-08-03
At a terminal, do:
```
sudo rm ~/.local/share/Trash/files/ -r
sudo rm /root/.local/share/Trash/files/ -r
```And see if this still comes.

---

### Post by alsamman on 2008-08-04
> **LinuxIsInnovation said:**
> At a terminal, do:
```
sudo rm ~/.local/share/Trash/files/ -r
sudo rm /root/.local/share/Trash/files/ -r
```And see if this still comes.

hey thanks, but it still has this problem. This has been a problem ever since I wanted to fix the trash applet on AWN so that when I right click on a file and click Move to Trash, it would move to the AWN trash bin.

---

### Post by alsamman on 2008-08-05
bump

---

### Post by alsamman on 2008-08-06
double bump

---

### Post by chunchengch on 2008-08-06
try this command,

[COLOR="Red"]$ ln -s ~/.local/share/Trash/files ~/.Trash
[/COLOR]

---

### Post by RayVad on 2008-08-25
Hi Alsamman,

Did you succeed in solving this problem?
I do have the same problemen as long as i'm using AWN here on Hardy Heron.

---

### Post by kaivalagi on 2008-09-03
I have problems with the trash applet too, it never shows as full and when I empty trash using it nothing happens, the trash still stays

I know it's not a problem with my trash files as the gnome panel trash applet works just fine....

HELP! I don't want to have to use the gnome panel anymore :(

[COLOR="Blue"]Edit: this is a known bug

As chunchengch has said, doing the following to create a symlink at the old ~/.Trash location to the proper location sorts it out I think (note the removal of the old directory as well).

```
rmdir -r ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash
```

Once this is done, as long as you delete via the open option of the applet, trash info is correctly maintained.

There is a good discussion on it here: [https://bugs.launchpad.net/awn-extras/+bug/194431](https://bugs.launchpad.net/awn-extras/+bug/194431)
[/COLOR]

---

### Post by alsamman on 2008-09-06
> **kaivalagi said:**
> I have problems with the trash applet too, it never shows as full and when I empty trash using it nothing happens, the trash still stays

I know it's not a problem with my trash files as the gnome panel trash applet works just fine....

HELP! I don't want to have to use the gnome panel anymore :(

[COLOR="Blue"]Edit: this is a known bug

As chunchengch has said, doing the following to create a symlink at the old ~/.Trash location to the proper location sorts it out I think (note the removal of the old directory as well).

```
rmdir -r ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash
```

Once this is done, as long as you delete via the open option of the applet, trash info is correctly maintained.

There is a good discussion on it here: [https://bugs.launchpad.net/awn-extras/+bug/194431](https://bugs.launchpad.net/awn-extras/+bug/194431)
[/COLOR]

I fixed this problem already regarding having both awn trash and the real trash correctly maintained. However, the error I am talking about is after I got the trash applet to work properly, whenever I right click on the applet and click empty, I get that screen that I uploaded in my original post. The problem is that that screen doesn't go away, I always have to click that Cancel button.

---

### Post by kaivalagi on 2008-09-06
> **alsamman said:**
> I fixed this problem already regarding having both awn trash and the real trash correctly maintained. However, the error I am talking about is after I got the trash applet to work properly, whenever I right click on the applet and click empty, I get that screen that I uploaded in my original post. The problem is that that screen doesn't go away, I always have to click that Cancel button.

Using the empty feature of the trasher applet is something that will not work, take a look at the details in the launchpad bug here: [https://bugs.launchpad.net/awn-extras/+bug/194431](https://bugs.launchpad.net/awn-extras/+bug/194431)

Trasher uses the old method of handling trash, rather than the new gnome process, and so if used to empty it (even after the symbolic link for .Trash is added) not all the trashing process is done completely...better to steer clear of emptying trash using the awn applet...

---

### Post by JustAboutRealJAR on 2008-10-03
for a more elegant solution, which will also allow you to use the stacks trasher... open your /etc/fstab file:

```
$ gksu gedit /etc/fstab
```

and add the following code to the end:

```
/home/<username>/.local/share/Trash/files /home/<username>/.Trash none bind
```

don't forget to replace <username> with your actual username ;)

if you want to make it work right now! with no reboot...

```
$ sudo mount -a
```

---

