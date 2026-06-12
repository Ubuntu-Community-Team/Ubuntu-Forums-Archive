---
title: "Kiosk Lockdown Mode Even Possible?"
date: 2005-11-21
forum: General Help
---

### Post by SuperMike on 2005-11-21
I want to have Ubuntu boot up for a timecard system that we have, which is a very simple webpage -- no Flash, Java, etc. Just Javascript and HTML.

The ideal system would boot up and have a timer on bootup. If you press CTRL+C in that timeframe, you can login as root. If you let it go or don't type in the proper root password, it just boots up as the default user, which is "timecard".

The timecard user boots without gdm or GNOME desktop, directly into Firefox.

Firefox will be locked down such that nothing is available except Home, Refresh, Stop, and Back. No URL or anything else is available. The user won't be able to do view source or any other magic keystroke to make it do bad things. Home will default to the timecard site.

Although GNOME and GTK+ will be installed, I want it to be simply X. The window manager will be gone -- so no titlebars, window maximization, tiling, cascading, etc.

Most bad keystrokes will be disabled, like CTRL+ALT+Fx, CTRL+ALT+BACKSPACE, etc.

To shut the thing down, one has to power it off hot and let it boot back up again.

Anyone done something like this?

---

### Post by SuperMike on 2005-11-29
Here's what I plan to do with Breezy to make it a web-based timecard kiosk. If you know how to do any of these things please let me know. If there's anything I say below with [GOT THIS], and you want me to explain how I did it, just reply and ask and I'll reply with the answer. Otherwise, I'm looking help for the items marked [NEED THIS]. Thanks!

* It boots up and goes to the GDM. However, I have edited the xinit file so that I disable CTRL+ALT+BACKSPACE and CTRL+ALT+Fx  [GOT THIS]

* The GDM asks for login. If you login with "timecard", password "timecard", it goes into GNOME.  [GOT THIS]

* Would love to have it so that if you wait at the GDM login for 30 seconds and don't do anything, it will autologin with "timecard". [NEED THIS]

* Once inside GNOME, somehow it needs to:

- Copy over the firefox settings again [GOT THIS]

- Kill process for gnome-panel [NEED THIS - Unfortunately, I think it comes back, doesn't it? How to keep from autoloading again?]

- Disable ability to rightclick the desktop [NEED THIS]

- Launch Firefox. [GOT THIS]

- I've added the extension that locks down Firefox into a kind of kiosk mode. [GOT THIS -- Symbio add-on extension]

- Goes to homepage with timecard web app [GOT THIS]

- Sends F11 using XMacroPlay to put timecard webpage in full screen mode. [GOT THIS]

- If command line or Nautilus could be invoked, restrict the timecard's access to anything beyond their own home directory. [NEED THIS]

- Disable timecard's access to sudo. [NEED THIS]

- Waits in a loop to detect if someone shuts down Firefox. If someone does, it automatically reloads it again after 10 seconds of waiting. [GOT THIS]

- Added a firewall to only allow certain incoming ports [GOT THIS]

- Got any other suggestions to lock this down more? [NEED THIS]

- Only way to get out of this is to reboot the box hot.

---

### Post by SuperMike on 2005-12-01
I found out how to configure a minimal proxy with Squid on my timecard kiosk. Here's the steps I used:

(I take it you know how to use vi. If not, download 'ne' and replace 'vi' in statements below with 'ne'. Then, hit Esc when you want a menu option.)

```

sudo vi /etc/apt/sources.list
# uncomment universe entries
sudo apt-get update
sudo apt-get install squid
sudo vi /etc/apt/sources.list
# comment universe entries back again
sudo apt-get update
# fix a little known squid crash problem in Ubuntu
sudo chmod -R a+rw /var/spool/squid
sudo mv /etc/squid/squid.conf /etc/squid/squid.conf.default
sudo vi /etc/squid/squid.conf
```

Now I put the following -and only- entries in squid.conf:

```

# OFFICE ONE-APP KIOSK SQUID SETTINGS

# DECLARE THAT ALL OTHER SITES ARE BAD
acl all src 0.0.0.0/0.0.0.0

# DECLARE AND ALLOW ONLY ONE APP
acl timecard_access dst timecard.mycompany.com
http_access allow timecard_access

# DENY EVERYTHING ELSE
http_access deny all
http_reply_access allow all

# PERMIT OUR SWAP FILE
coredump_dir /var/spool/squid


```

And now you set Firefox to use a proxy in its preferences and point it to 127.0.0.1 on port 3128 for all ports.

And now you bounce your proxy:

```

sudo /etc/init.d/squid force-reload
sudo /etc/init.d/squid restart

```

And now your Firefox can only go to timecard.mycompany.com.

---

### Post by RAOF on 2005-12-01
[QUOTE=SuperMike]
- Kill process for gnome-panel [NEED THIS - Unfortunately, I think it comes back, doesn't it? How to keep from autoloading again?]

- Disable timecard's access to sudo. [NEED THIS]
[/QUOTE]
1) Won't the session manager allow you to remove gnome-panel from timecard's session?  I seem to remember accidentally doing this sometime :)

2) Remove timecard from the "admin" group.  Only users in the "admin" group have sudo access by default.

---

### Post by huwshimi on 2005-12-01
[QUOTE=SuperMike]Would love to have it so that if you wait at the GDM login for 30 seconds and don't do anything, it will autologin with "timecard". [NEED THIS][/QUOTE]

Hi SuperMike,
The following link will explain how to have gnome automatically log in. There might also me some other useful info on that site for you.

[http://ubuntuguide.org/#automaticlogingnome]("http://ubuntuguide.org/#automaticlogingnome")

Cheers

---

### Post by SuperMike on 2005-12-02
Disabling Special X Windows Keystrokes

I found that disabling CTRL+ALT+BACKSPACE might not be really suitable because you may want to walk up to the kiosk and have a way to login as root without reboot. And, especially if you edit /etc/gdm/gdm.conf and change the timed login parameters, you really don't have to worry that much about someone doing CTRL+ALT+BACKSPACE and forcing it to the login screen all the time. I mean, with the gdm.conf changes, you'll ensure that within 30 seconds it will login the timecard user.

You may, however, disable the CTRL+ALT+Fx keys. To do that requires editing /etc/X11/xorg.conf and adding in:

```
Section ServerFlags
    Option "DontVTSwitch" "true"
EndSection
```

However, if you *do* want to disable CTRL+ALT+BACKSPACE as well, do this:

```
Section ServerFlags
    Option "DontVTSwitch" "true"
    Option "DontZap" "true"
EndSection
```

Moreover, someone could bungle the video mode with CTRL+ALT+KEYPAD MINUS/PLUS. So, you should do:

```
Section ServerFlags
    Option "DontVTSwitch" "true"
    Option "DontZap" "true"
    Option "DontZoom" "true"
EndSection
```

---

### Post by SuperMike on 2005-12-02
Securing Firefox

My steps here don't lock Firefox down altogether, but they do frustrate the casual user. Also, if the system were to ever be logged out and back in again, anything that someone has bungled will be undone.

1. The first thing to do is to set a proxy on the web browser, as I have mentioned in this thread. A self proxy on a kiosk can take up a lot of time to figure out. Fortunately I have explained how to do this already in this thread.

2. At first I tried the Symbio Firefox chrome extension that's supposedly designed for kiosks, but it's not designed well for this kind of kiosk where you only want to run one web app and you don't want people messing with the URL. So, actually, I quit using it and uninstalled the extension. I found something a little better....

3. Next, I opened up Firefox and right-clicked the menubar and started customizing it. I removed buttons and other features the user should not use with drag and drop. Of course, a user could eventually add them back, but I fix that later on here in another step.

4. I set the homepage to exactly where I want it -- the kiosk web app.

5. I set all other preferences I desired inside Firefox, including forgetting of history, passwords, form field history, etc.

6. I opened the Sessions applet in Gnome and set the default login to run "startup.sh" script.

7. In the startup.sh script, I set it to launch firefox with the " &" option on the end so that the script can detach itself from that process, and then I did "sleep 5", followed by a set of xmacroplay commands. The reason for the xmacroplay commands is to put firefox into full screen mode with the F11 key. To do that, however, is a little tricky and requires that you first install xmacro (a universe download from apt sources), and then record keystrokes for ALT+TAB and F11. Since xmacro doesn't come with a man page, here's how to do that:

```
sudo vi /etc/apt/sources.list
# uncomment the universe option, save, and exit
sudo apt-get update
sudo apt-get install xmacro
sudo vi /etc/apt/sources.list
# comment the universe option, save, and exit
sudo apt-get update
xmacrorec2 > startup.keys
# press Esc key
# press ALT+TAB
# use mouse to flip back to command line
# press F11 and ignore funky characters on screen
# press Esc key
# press backspace key because it has put a funky character on the screen
# ignore what you see and then do...
vi startup.keys
# get rid of the MotionNotify and ButtonPress lines. you only want lines beginning with "KeyStr".
# test your command now with:
firefox &
# to launch your browser if it is not open
cat startup.keys | xmacroplay ":0.0"
# this should flip from your command window to firefox and switch firefox to full screen mode.

```

And so, with that done, I could edit my startup.sh file and append, after a "sleep 5" command, the *cat startup.keys | xmacroplay ":0.0"* statement so that Firefox gets switched to full screen mode.

8. Next, I edited startup.sh so that it recopies over the entire "/home/timecard" directory (including hidden files) from a backup, blowing away any changes and putting settings the way they should be.

9. Next, I added the extension into Firefox that is the 5 minute timer so that the app gets reset back to the homepage if idle. This is in the firefox kiosk extensions.

10. Next, I changed startup.sh so that it sits in a loop after the xmacroplay and waits for the death of the firefox app in memory. When it detects it, it relaunches it again. I do that with a Bash loop, a process check with pstree, grep, sed, and test, and then launch firefox if need be.

11. Next, I locked down Gnome, which I will explain in another follow-up post.

So, with all of this, I'm able to have Gnome autologin, launch firefox in sort of a restricted mode (for the casual user), and then put it in full screen mode. If the user tries to change something, it will only last as long as the login. When the system is logged out and back in again, all the settings are restored again. If the user is idle in the web app for 5 minutes, it will reset to the homepage. It's not foolproof, but it's a step in the right direction.

However, saying all of this, it's too bad that you can't do this:

firefox --kiosk-mode-1 # for a one-app kind of kiosk where users can't change anything and can only do Refresh and Home

or

firefox --kiosk-mode-2 # for a kiosk with with an addressbar so that they can surf, but they can't change any other settings

And, as well, it's too bad you cannot have a "--one-domain" switch so that Firefox has a kind of self-proxy installed so that you can only surf on one ".com", or ".net", or ".org", etc., depending on what's listed in the homepage. That would keep admins from having to build and configure Squid.

And, as well, it's too bad you cannot have a "--auto-reload" so that if Firefox is ever shut down, it reloads itself.

---

### Post by SuperMike on 2005-12-02
For locking down Gnome, I found a handy guide here:

[URL="http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/index.html"]http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/index.html
[/URL]

It works sort of okay in Ubuntu Breezy on most stuff. Haven't tried it in Hoary, but would imagine it would work there too.

---

### Post by ashrack on 2006-05-09
Hello! 
Im also trying to do a similar thing. Locking down GNOME but am stuck at :```

8. Next, I edited startup.sh so that it recopies over the entire "/home/timecard" directory (including hidden files) from a backup, blowing away any changes and putting settings the way they should be.
```

How did U achieve this? And I mean everything what type of script did U write and where did U put it...
tanx

---

### Post by SuperMike on 2006-05-11
ashrack:

1. When you get your timecard dir just perfect, back it up either into another directory like /home/timecard2 (not mapped to a user timecard2, mind you), or back it up into a tar.gz file (with tar and gzip commands) into some place like /var.

2. Put your Bash script in /etc as "rewrite_timecard.sh". Use the cp command in that script to copy from /home/timecard2 to overwrite /home/timecard without asking any questions. If you do 'man cp', you can see how that's done.

3. Call this script from the Main Menu\System\Preferences\Sessions control panel. Add it in under the tab "Startup Programs".

---

