---
title: "reinstall using terminal??"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by jonnyg01 on 2009-10-12
I had a black box problem in that when i was tweaking compiz, i think i clicked on the cube option and big black boxes started taking over the screen and i couldn't click anything.

i've resulted to booting from the disk, but i can only use the terminal and i dont have much experience on it.

my question is, how do i use the terminal to boot from the cd?

ps. if i go into the bios, and make the cd boot first other than the hd, it gives "disk boot error. insert system disk and press enter." and repeats each time i press it.

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> I had a black box problem in that when i was tweaking compiz, i think i clicked on the cube option and big black boxes started taking over the screen and i couldn't click anything.

This isn't useful information, "I think". Anyway, ...

> i've resulted to booting from the disk, but i can only use the terminal and i dont have much experience on it.Rename offending folder 
mv <folder-with-settings> new_name (may be a hidden folder - one which begins with a DOT) and startx.

> my question is, how do i use the terminal to boot from the cd?You don't ... see your answer below.

> ps. if i go into the bios, and make the cd boot first other than the hd, it gives "disk boot error. insert system disk and press enter." and repeats each time i press it.You need a bootable disk. One you're trying isn't bootable.

On second thought ... you can put all your files (include the hidden) in a folder and startx. And, if you really think a re-install is needed (I doubt it is), you'll need to deal with your user configurations files nonetheless - unless they are all in a folder for later copying - EXCLUDING the goofed config settings!. BUT, to re-install what? xorg? GNOME, KDE, XFCE4? You didn't say. The WHOLE system? Why the system? Remove compiz? OK, apt-get remove compiz, startx and deal with the errors, if any.

---

### Post by jonnyg01 on 2009-10-12
i brought up the black boxes because i think fixing that would be easier than "pulling the files into one folder" due to the fact that i don't know how to do that.

i did, in fact, mean reinstalling the whole OS because i have no idea how to use the terminal for looking for whats wrong...

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> i brought up the black boxes because i think fixing that would be easier than "pulling the files into one folder" due to the fact that i don't know how to do that.

i did, in fact, mean reinstalling the whole OS because i have no idea how to use the terminal for looking for whats wrong...

There are many ways, as you know, to skin a kitty cat ... they all get him done. Impression I have is you'd prefer not to re-install but learn how to fix a small problem. If I'm right, your best option, IMO, is to rename the offending folder, or autostart file, so it's config file isn't loaded. However, if you have the "I can't learn that for I'm a MS zombie" attitude then you're gonna need a bootable LiveCD. Either way, you'll need to _learn_ to 

A) rename a folder or file[INDENT]or
[/INDENT]B) setup cd burner in tty with apt-pet, aptitude or dpkg, get an ISO with links2 or the like, or with wget, learn to burn gotten ISO to CD, as other than an ISO, in tty and boot it.

What do you choose?

Want another option? C?

Okay. Login as root, if you know how, do one of the above - remember to chown your folders and files if needed. Make fixes.

---

### Post by BQAggie2006 on 2009-10-12
Instead of booting from a CD, trying booting into Single User Mode. When the GRUB menu comes up, hit ESC to go into the boot options, select Recovery Mode, and hit Enter. When presented with the Recovery Menu, scroll down to select root then hit Enter. Once you are given a command prompt, run the following command:

```
metacity --replace
```This will replace Compiz as the window manager with the default Metacity window manager and should hopefully get rid of your black boxes.

---

### Post by rippin on 2009-10-12
> **BQAggie2006 said:**
> Instead of booting into a CD, trying booting into Single User Mode. When the GRUB menu comes up, hit ESC to go into the boot options, select Recovery Mode, and hit Enter. When presented with the Recovery Menu, scroll down to select root then hit Enter. Once you are given a command prompt, run the following command:

```
sudo metacity --replace
```This will replace Compiz as the window manager with the default Metacity window manager and should hopefully get rid of your black boxes.

Another good idea! Let's see what OP will do. Hmmm....

---

### Post by jonnyg01 on 2009-10-12
Ok, i choose option A. Would or could you tell me how to find the problem folder and then how to rename it?

---

### Post by rippin on 2009-10-12
> **BQAggie2006 said:**
> Instead of booting from a CD, trying booting into Single User Mode. When the GRUB menu comes up, hit ESC to go into the boot options, select Recovery Mode, and hit Enter. When presented with the Recovery Menu, scroll down to select root then hit Enter. Once you are given a command prompt, run the following command:

```
sudo metacity --replace
```This will replace Compiz as the window manager with the default Metacity window manager and should hopefully get rid of your black boxes.

I use XFCE4. So, what I'd like to learn from you is, is this like using a shot gun (affecting entire system) when a pistol would be better (user executing this on his files alone)?

---

### Post by jonnyg01 on 2009-10-12
just tried the the metacity replace and it reads underneath..."Window manager error: Unable to open X display"

---

### Post by BQAggie2006 on 2009-10-12
You could also try the xfix option in the Recovery Menu. It attempts an automatic repair of any graphics problems.

---

### Post by BQAggie2006 on 2009-10-12
Rippin,
I think moving all of the user config files into another folder and/or doing a full re-install would be the shotgun approach. If the problem started after compiz was enabled, then it seems (IMO) like the best option would be to go back to the last known good configuration by disabling compiz.

---

### Post by jonnyg01 on 2009-10-12
> **BQAggie2006 said:**
> You could also try the xfix option in the Recovery Menu. It attempts an automatic repair of any graphics problems.
i've already tried that. i think its more of an application problem, rather than a graphic problem.  it might also be the graphics i'm trying to enhance while using a card that cant handle it.

my card is a....actually i never bought a graphix card, but i do have an Abit iL-90MV motherboard...any thoughts?

---

### Post by rippin on 2009-10-12
> **BQAggie2006 said:**
> Rippin,
I think moving all of the user config files into another folder and/or doing a full re-install would be the shotgun approach.

I'm NOT advocating a re-install. How is a user fixing his files alone, not affecting the entire system, bad?

>  If the problem started after compiz was enabled, then it seems (IMO) like the best option would be to go back to the last known good configuration by disabling compiz.What about my question? Why *can't* a user, or why *shouldn't* the user,  do the command on his files alone?

---

### Post by jonnyg01 on 2009-10-12
d

---

### Post by jonnyg01 on 2009-10-12
ok so rippin, how to i locate and pull the files??

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> ok so rippin, how to i locate and pull the files??

Which method do you want to first try? As root, and changing file permissions, or your user and your files?

---

### Post by jonnyg01 on 2009-10-12
lets go with my user and my files:)

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> lets go with my user and my files:)

I'm guessing you're using GNOME as you tried "--metacity". Simplest is to rename your ~/.gnome* folders to no DOT. This will leave you with the fresh GNOME desktop. From there you can tweak away! <G>.

Renaming doesn't need to be recursive in this case. Plus, renaming, using the mv command, keeps your data for copying after repair. This method will work with KDE as well - change the folder name. 

Since I'm on XFCE4, you'll need to check for anything named ~/.gnome*, or ~/.compiz, etc.  (these are hidden folders). I DON'T USE COMPIZ, so you'll have to be the one carefully choosing what to rename. But, remember, all data is still there for later use. Should you not know, "~/" represents your user's /home . I like complete paths to avoid errors.

ls ~/.gnom* (to see all hidden GNOME folders and files; ignore ~/.gnome2_private)

We care only about top-level folders, no subs:

ls -a ~/.gnome*
/home/cmo/.gnome2: (top level)
.  ..  accels  evince  gnomesword  keyrings (not top-level)

/home/cmo/.gnome2_private:  (empty top-level place holder - ignore)
.  ..

Dealing with folder names only, sort out  and do as such:

mv ~/.gconf gconf (notice, removing the DOT only)
mv ~/.gnome2 gnome2

By making them non-DOT, GNOME will asume a new desktop and start your GNOME settings afresh.

info mv

MV(1)                            User Commands                           MV(1)

NAME
       mv - move (rename) files

SYNOPSIS
       mv [OPTION]... [-T] SOURCE DEST
       mv [OPTION]... SOURCE... DIRECTORY
       mv [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.

I'm using "Rename SOURCE to DEST"; oldname to new-name.

Then you can startx followed by tweaks.

Standing by,

---

### Post by jonnyg01 on 2009-10-12
to begin, do i go into recovry and root? or go to the terminal at the login page?

---

### Post by jonnyg01 on 2009-10-12
and im stuck at the rename source to dest" part...can you clarify?

---

### Post by jonnyg01 on 2009-10-12
i followed all the steps up until "rename source..." started up my computer and it worked!!!!!!! im going to restart it to make sure it sticks the head to work in a very happy mood. 

thank you so much ripper!

Jonnyg01

---

### Post by jonnyg01 on 2009-10-12
no homo...i love you

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> no homo...i love you

LMAO ! No problem.:popcorn:

Think I confused you posting the 'man' page for 'mv'. No need to worry about destination at this point.

Wishing you well,

---

### Post by rippin on 2009-10-12
> **jonnyg01 said:**
> to begin, do i go into recovry and root? or go to the terminal at the login page?

Do a usual boot and common login ... no need for root as you own the folder/files.

---

