---
title: "gutsy: Intel graphics laptop mirrored LCD + external projector?"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by cayhorstmann on 2007-10-16
I just upgraded to Gutsy, and now I can't get an external projector (or monitor) to work. I have a Thinkpad X60 with Intel graphics. I use the experimental modesetting driver (intel), not the i810 driver (which doesn't get me the 1440x1050 resolution of my laptop panel). 

When I select System->Administration->Screen and Graphics, I get a dialog that supposedly lets me configure two screens (LCD and external, I presume), but the "secondary screen" and the option of mirroring is always grayed out. How do I activate these? When giving a presentation, I must be able to view my laptop screen and have an identical external output.

Thanks,

Cay

---

### Post by jmaryinchina on 2007-10-17
Concerning my experience that new utility is totally ****** up, the best result I have seen with is at clicking Cancel and especially to not test the setting I could make.

I resume that dramatic story by :
Edgy : I could configure (with pain) a working dual screen, 2048x768
Feisty : I had to choose either to use the laptop screen or only the external screen.
Gutsy : Now only the laptop screen works as expected.

Conclusion : I might go back to edgy, because the more work is done with X, better the mess is.

It's totally catastrophic !!!

I expect to have no display at all with Ubuntu  8.04. It's reasonable.

---

### Post by cayhorstmann on 2007-10-17
The test button is always grayed out for me--maybe that's a good thing? 

What determines what is grayed out? Why can't I set a secondary screen?

---

### Post by erikringmar on 2007-10-24
Hiya,

Just to register my displeasure re the same issues.  I happily used Feisty at my university (although the PC screen didn't work at the same time as the projector),  but now I have to resort to asking one of my students if they brought a MS computer.  How embarrassing is that?

Please someone, help us!!!

yours,

Erik

---

### Post by jis on 2007-10-24
According to 
[http://www.ubuntu.com/getubuntu/releasenotes/710tour](http://www.ubuntu.com/getubuntu/releasenotes/710tour)
Ubuntu Gutsy has something called Dynamic screen configuration.

See "Dual-head (multi-screen) setups" here:
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

### Post by cow_racer on 2007-10-24
For me, I connect the external monitor to the laptop, thenI kill gnome by ALT+CTRL+BACKSPACE.  When gdm starts, video is mirror to both monitor.

I'm using ATI x1400.  So, i don't know if that will make a difference.  But I know it works even when I'm using vesa instead of fglrx.

---

### Post by dietrying on 2007-10-24
try using the i810 driver. Works for me very good like it does in feisty

---

### Post by jis on 2007-10-25
Screens and Graphics won't store the driver change to i810. When the dialog does overwrite xorg.conf?

I've got Mobile Intel 910GML Express chip with Intel GMA 900. I used i810 together with 915resolution in Feisty; so I got external monitor work with right resolution in Feisty.

---

### Post by dietrying on 2007-10-25
i'd recommend to use

dpkg-reconfigure xserver-xorg

and not the graphic tool.....it's buggy
greetings,
David:guitar:

---

### Post by jis on 2007-10-25
More than 100 bugs reported about the graphical tool - displayconfig-gtk - in Launchpad!

---

### Post by garton on 2007-10-25
> **jis said:**
> More than 100 bugs reported about the graphical tool - displayconfig-gtk - in Launchpad!


That's not true. There are 20 bugs reported in Launchpad, out of which 

4 are requests for translations, or translation related
2 are cosmetic bugs that doesn't affect functionality

So in essence, there are 14 bug reports on this application, not more than 100.

---

### Post by tschneiter on 2007-10-25
The way to get this done in gutsy using the intel driver is with xrandr.

type 'xrandr' at your terminal, and you'll get a list of connected devices and their potential resolutions.

You need to add another line to your xorg.conf "screen" subsection "display"
```
virtual x y
```
where x and y are the maximum resolutions you'll be using in the x and y coordinates

```

#this will turn on your external monitor
xrandr --output VGA --auto

#this will mirror your laptop monitor
xrandr --output VGA --same-as LVDS

#this will turn off your external
xrandr --output VGA --off

```

This should work... check xrandr --help for a list of options.

---

### Post by jis on 2007-10-25
> **garton said:**
> 
So in essence, there are 14 bug reports on this application, not more than 100.

If I do a simple "displayconfig-gtk" bug search in [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) I get much more, but not all of them are displayconfig-gtk bugs, I suppose. Only one bug has future Target milestone set, namely bug [151647]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/151647"); the milestone is Ubuntu: gutsy-updates.

---

### Post by Lil on 2007-10-25
Just a heads up for the Intel folks.

Screens and Graphics does not configure dual screens for those of us using Intel or Radeon open drivers, as Screens and Graphics configures dual screens using Xinerama which the Intel and Radeon drivers have now dropped support for. The problem is, this is not highlighted enough, then you need to know what Xinerama even is! Not exactly for humans... Anyway I digress...

Instead your best bet is probably something called xrandr.

I wrote a blog entry here:

[http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/](http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/)

This is a program I made for my ThinkPad T40 with a Radeon 7500 so it'll need some tweaks for Intel Integrated as the output names are different to the Radeon (e.g. I don't think the VGA port is referred to as VGA-0) but none the less, you are free to read that and the script and modify it to your hearts content.

Also a long thread here should guide you:

[http://ubuntuforums.org/showthread.php?t=580967](http://ubuntuforums.org/showthread.php?t=580967)

And more still here: [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

Really hope this gets you in the right direction.

Update: If you download my script from my blog, you will need to change the entries for VGA-0 to just VGA on Intel graphics, then it should work fine. Same with my blog instructions, where i would have written something like:

xrandr --output VGA-0 --auto

You should instead use:

xrandr --output VGA --auto

Vicky

---

### Post by dysphasi on 2008-01-09
I know the thread is a couple of months old, but wondering if anyone here had any idea on how to go about enabling any kind of overscan using an intel card?

---

