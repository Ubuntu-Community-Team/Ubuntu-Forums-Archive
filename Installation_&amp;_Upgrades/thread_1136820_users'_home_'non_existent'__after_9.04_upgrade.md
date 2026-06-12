---
title: "users' home 'non existent'  after 9.04 upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2009-04-25
I had to install a localized version of Ubuntu on the old PIII box that I use mainly as guests' desktop, because most of those who would use it don't know enough English, so I can't post the exact error messages because they would be in another language. Hopefully I'll be able to make you understand what I'm talking about.

The PIII box used to run Ubuntu 8.10 x86 that was installed straight off the CD, the HDD is partitioned in 3 primary partitions: one for /home, one for swap and one for / and everything else.

Last night I ran the update manager to upgrade to 9.04 but I had to abort while the packets were being downloaded because the server box that works as a router (among other things) crashed because of an "error between keyboard and chair" (come on, don't tell me that you never do anything stupid)

After fixing the server/router I restarted the update manager and the upgrade seemed to be fairly well, except for the usual problems with the nVidia drivers (the upgrade tool didnt install the restricted drivers or any restricted modules, even tho I did have those installed before the upgrade)

So I installed the missing packages but at some point while I was installing/uninstalling stuff and rebooting several times (it took me a while to figure out what happened) the system started pop up a weird message.

Right after boot and before auto-login into the default user's account (which is _not_ the sudo-enabled main user) an error message would show up, reading something like this: 

"The user's home directory is set up to be /home/<username>, but it doesn't seem to exist. 
Do you want to use  /root as home directory?
It is unlikey that anything will work, unless you use an emergency session"

And then the usual yes/no choice.

Clicking 'yes' the system would try to auto-login into the default user's account and end up in a one-color screen (the background color under the wallpaper). Nothing would get me oout of there, not even crtl-alt-backspace, so I had to use the reset button.

Next try: at the 'want to use /root as /home' prompt I clicked 'no'. The system popped up the login window (didnt try to auto-login despite being set up to do so) but trying to log in would end up in the same monochrome screen, no matter what user (main or default) I tried to log in as.

So after next reboot I tried to click 'no' again but instead of trying to log in, I went to the login screen's "Actions" menu and chose 'reboot'.
The system rebooted, the 'root-as-home' prompt did not pop up and the default user auto-logged in. Everything worked perfectly including nVidia drivers and Compiz.

When I rebooted from the start menu, the problem showed up again.
Now I can use the box and everything work, but at each startup I have to boot up twice: first into the root-as-home prompt and choose 'no', then choosing 'restart' off the 'Actions' menu, and at that point everything works. 

Does anyone know what is going on and how I fix it?

---

