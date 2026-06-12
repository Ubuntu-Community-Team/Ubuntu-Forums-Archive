---
title: "installing a theme..."
date: 2008-07-27
forum: General Help
---

### Post by scotcella on 2008-07-27
I have looked at a few threads... and I'm still not very clear how to install themes...

I downloaded this [theme]("http://gnome-look.org/content/show.php/%22Aqua+Dreams%22+theme?content=72997") found on gnome-look (I think)... 

I extracted it onto my desktop for the time being..  

Two things I am finding confusing is...

In the read me in this folder.. 

> You must have install Grub-gfx, and test it before installing this theme

The code for this is

```
sudo mv /home/your_login/AquaTheme-1.0/grub-gfx/message.aqua /boot/grub/message.aqua

# I changed the login name to ella and the updated file name to 1.3

sudo mv /home/ella/AquaTheme-1.3/grub-gfx/message.aqua /boot/grub/message.aqua
```

The terminal comes back with "No such file or directory".



Now the other way i've been reading about installing themes by dragging and dropping into System -> Preferences -> Appearences gets bounced back with that the file is not a valid theme.

So I'm a bit confused.

I have installed compiz and its running beautifully..  I love it...

Any help appreciated..  I hope I put in relevent information to my confusion

---

### Post by BLTicklemonster on 2008-07-27
Ah there's an install english file you need to read in the folder that extracts.

---

### Post by scotcella on 2008-07-27
Thats what I am reading.. which is why im asking for more help

---

### Post by xcesarfrancox on 2008-07-28
You said in the first post that you downloaded the file to your desktop, verify the path:

Try with this one:
```
sudo mv /home/ella/Desktop/AquaTheme-1.3/grub-gfx/message.aqua /boot/grub/message.aqua
```

---

### Post by scotcella on 2008-07-28
> **xcesarfrancox said:**
> You said in the first post that you downloaded the file to your desktop, verify the path:

Try with this one:
```
sudo mv /home/ella/Desktop/AquaTheme-1.3/grub-gfx/message.aqua /boot/grub/message.aqua
```


The output of that wasn't much better........  which was...

```
mv: cannot stat `/home/Ella/AquaTheme-1.3/grub-gfx/message.aqua': No such file or directory

```

:(:(

Is anyone able to help me....?

I'm still stuck..


The first instructions to installing this theme (copied and pasted directly from the readme...

> * Grub-gfx

You must have install Grub-gfx, and test it before installing this theme. If you want you can find some informations on this website: [http://doc.ubuntu-fr.org/grub-gfx](http://doc.ubuntu-fr.org/grub-gfx)
It's very easy, open a terminal, make:
$ sudo mv /home/your_login/AquaTheme-1.0/grub-gfx/message.aqua /boot/grub/message.aqua
Edit your /boot/grub/menu.list add
gfxmenu (hdX,Y)/grub/message.aqua 
just before the line ## ## End Default Options ##
Save and exit
Reboot

---

### Post by xcesarfrancox on 2008-07-28
First do the following, place the AquaTheme-1.3 folder on your home, I mean: /home/ella (remember that all commands are case sensitive, so if your username is Ella and not ella, this is a problem)

when you have /home/ella/AquaTheme-1.3/ the open a terminal and cd to it:
```
cd ~/AquaTheme-1.3/
```

then do this:
```
sudo mv grub-gfx/message.aqua /boot/grub/message.aqua
```

As for this theme, to install the gtk you need to do this:
```
cd ~/AquaTheme-1.3/
cp -r Gtk/ZgegBall-aqua/ ~/.themes/
```

Hope it helps

---

### Post by UbuntuNerd on 2008-07-28
sorry

---

### Post by UbuntuNerd on 2008-07-28
?

---

### Post by xcesarfrancox on 2008-07-28
@UbuntuNerd: What does emerald have to do with grub??? This guy has a problem with copying this theme's message.aqua (GRUB-GFX theme) to /boot/grub, I don't see anything related to emerald here...

---

### Post by UbuntuNerd on 2008-07-28
sorry my fault I miss understood her

---

### Post by MuziKid on 2008-07-29
ummm...idk if im just stupid or what, but i don't think there's any files in "/AquaTheme-1.3/grub-gfx"

that could be the issue. idk if that is or not tho, i just started using linux.

---

### Post by xcesarfrancox on 2008-07-29
> **UbuntuNerd said:**
> sorry my fault I miss understood him

It's alright dude, I apologize if a was rude or someting, is just that this guy is confused and talking him about emerald when his problem is related to grub is going to confuse him more, lol

> **MuziKid said:**
> ummm...idk if im just stupid or what, but i don't think there's any files in "/AquaTheme-1.3/grub-gfx"

that could be the issue. idk if that is or not tho, i just started using linux.

Is this folder empty in your download??? I downloaded it to be able to give support and there's actually the file... but I haven't been able to get grub-gfx to work...

@scotcella: How are you doing?? can you give some feedback please?

---

### Post by UbuntuNerd on 2008-07-29
hey didn't want to confuse anyone but for some reason this all I was able to see from her original post my bad 



"I have looked at a few threads... and I'm still not very clear how to install themes...

I downloaded this theme found on gnome-look (I think)...

I extracted it onto my desktop for the time being..

Two things I am finding confusing is...

In the read me in this folder.. "


then later I realized what your were talking about I feel like and idiot

---

### Post by UbuntuNerd on 2008-07-29
anyway if you still want to give it one more try check out this guide 


[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/")

---

### Post by scotcella on 2008-07-30
> **UbuntuNerd said:**
> hey didn't want to confuse anyone but for some reason this all I was able to see from his original post my bad 



I'm a SHE :lolflag:

Anyway, thanks for your replies..  maybe it's the theme file itself that's the issue. I downloaded some other themes and they were fine and had no issues installing them.

:popcorn:

---

### Post by UbuntuNerd on 2008-07-30
sorry girl good luck by the way I just try the guide I posted for you and it worked fine !!!

---

### Post by xcesarfrancox on 2008-07-30
@UbuntuNerd: no problem! we're all just here to collaborate :) you just misunderstood, but no problem :)

@scotcella: I was able to install everything on that theme, although I didn't like anything so I switched back to what I had previously lol

But I did try and everything worked just fine, try the guide UbuntuNerd posted, it should work for you

---

