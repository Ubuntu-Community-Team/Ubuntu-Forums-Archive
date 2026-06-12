---
title: "need help with xfce/xubuntu"
date: 2005-11-03
forum: General Help
---

### Post by rplantz on 2005-11-03
(First, I apologize for posting this earlier with a misleading subject. I'm trying again with a better one.)

Last week I installed xfce and got it working. Then I switched back to gnome. Now I can't get xfce to run again.

I can select the xfce session before I log on, but it doesn't pay any attention to me. It simply logs on to a gnome session.

I reinstalled xfce. No changes.

I installed xubuntu. No changes.

I would like to be able to select which session I want each time I log on.

I had it working once. What have I screwed up?

Bob

---

### Post by ecobuntu on 2005-11-03
[QUOTE=rplantz](First, I apologize for posting this earlier with a misleading subject. I'm trying again with a better one.)

Last week I installed xfce and got it working. Then I switched back to gnome. Now I can't get xfce to run again.

I can select the xfce session before I log on, but it doesn't pay any attention to me. It simply logs on to a gnome session.

I reinstalled xfce. No changes.

I installed xubuntu. No changes.

I would like to be able to select which session I want each time I log on.

I had it working once. What have I screwed up?

Bob[/QUOTE]

Hmm...are you running gdm, xdm, or kdm? 
maybe try 
sudo apt-get install xubuntu-desktop (though it sounds like you already have)

---

### Post by rplantz on 2005-11-03
[QUOTE=ecobuntu]Hmm...are you running gdm, xdm, or kdm? 
maybe try 
sudo apt-get install xubuntu-desktop (though it sounds like you already have)[/QUOTE]

And how do I determine which I'm running?

Yes, I did try installing, and even reinstalling xubuntu-desktop.

Bob

---

### Post by eyebrowman92 on 2005-11-03
are you sure you picked xfce before you log on? if you dont specifically pick a session it will go to to the last session you used. make sure you're installing the latest version of xfce also which is xfce4. this is probably no use to you but have you tried ```
sudo apt-get install xfce4
```?

---

### Post by rplantz on 2005-11-03
[QUOTE=eyebrowman92]are you sure you picked xfce before you log on? if you dont specifically pick a session it will go to to the last session you used. make sure you're installing the latest version of xfce also which is xfce4. this is probably no use to you but have you tried ```
sudo apt-get install xfce4
```?[/QUOTE]

Well, all comments are welcome and useful.

I just tried doing a complete removal of all xfce4 and xubuntu stuff, then did an install of xubuntu-desktop, which brought a lot of xfce4 things with it.

Still doesn't work.

One of the things that's odd is that the session choices when I log on include xfce, not xfce4. And this choice did not go away even after I did a complete removal of all xfce stuff.

Frustrating, since it was working fine a few days ago.

Bob

---

### Post by ecobuntu on 2005-11-03
xfce = xfce4
how about looking into synaptic to see if GDM, XDM, or KDM is installed

---

### Post by rplantz on 2005-11-03
[QUOTE=ecobuntu]xfce = xfce4
how about looking into synaptic to see if GDM, XDM, or KDM is installed[/QUOTE]

Only gdm is installed. (:oops: A little embarrassing that I didn't think of synaptic.)

Bob

---

### Post by rplantz on 2005-11-04
I've tried several uninstall/install cycles. I still cannot get xfce4 running.

As I understand things, it's gdm which allows me to select my session. I have the choice between same as last time, default, gnome, and xfce. It doesn't matter which one I select. I always get gnome.

I'm guessing that it's an issue with gdm.

I know it's something silly that I'm missing, since I had it working fine just a few days ago.

Bob

---

### Post by tehwa on 2005-11-04
Do you have an entry for XFCE in the directory```
/usr/share/xsessions
```You should have an entry for GNOME, and an extra entry for XFCE. It should have an execution statement in there, check to see that the XFCE entry is not executing GNOME ```
Exec=/usr/bin/gnome-session
```That execution might be where the problem is.

---

### Post by rplantz on 2005-11-04
There was a problem in my xsessions directory. The entry in xfce4.desktop was
```

Exec=/usr/bin/startxfce4

```
(The exact names may have been a little different.)

I changed it to xfce4-session. I then saw the mouse, but the system just hung.

That led me on a purging expedition. I deleted all files I could find that had "xfce" in their names. I even got rid of the packages.

Then I installed xfce4 again. Still doesn't work.

This is really weird. As I recall, all I did last week was to install xfce4 through synaptic, and it worked. Perhaps I did something else to get it going?

Bob

---

### Post by rplantz on 2005-11-05
I finally got it working again.

I searched Synaptic for all xfce packages and reinstalled all of them.

One thing that is still broken is the xfce menu. It contains nothing. As I recall, it previously had quite a few items.

I shall continue my playing, but if anyone has some ideas about how I can restore xfce menu, I would appreciate hearing them.

Bob

---

