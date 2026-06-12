---
title: "FreeNX with broken keymap in 8.04LTS - no arrow keys"
date: 2008-10-26
forum: General Help
---

### Post by TheFinePrint on 2008-10-26
I just did a clean install of 8.04LTS on my desktop/home server.  Then I installed SSH and FreeNX.  However when I connect to my server with NXClient there are a lot of keys that simply are not correct.  In particular the arrow keys do not seem to work at all, and arrow-up takes a screenshot.

Home/PgUp/etc don't work at all.  But - all regular characters, numbers, enter and backspace works fine.  It's even the right keymap (norwegian), despite the physical keyboard on the machine is danish, and the machine-layout is danish. (ok confusing.  Here's how it is:)

server from server: danish (correct)
laptop from laptop: norwegian (correct)
server from laptop: norwegian (correct, but with broken keys).

Changing the keymap when in NX does not seem to work.  There are lots of reports of older versions of FreeNX not recognising the client-keymap, but that is apparently not the case here.  Any help would be much appreciated.


edit:
In the layout editor I have tried various different keyboard models, but it does not change anything.  I can also see where some of the buttons are mapped:
**Physical key - interpreted key**
Right arrow - nowhere
Left arrow - AltGr/ISO_L....
Down arrow - Right Super
Up arrow - Screenshot
Right Ctrl - Right Enter
AltGr - PgDn
PgDn - Right Menu
PgUp - Numpad Slash
Home - Pause
End - Left Super
Delete - nowhere
Left super - nowhere
Menu - nowhere

The rest seems to be correctly mapped.

---

### Post by muken on 2008-10-27
> **TheFinePrint said:**
> 
**Physical key - interpreted key**
Right arrow - nowhere
Left arrow - AltGr/ISO_L....
Down arrow - Right Super
Up arrow - Screenshot
Right Ctrl - Right Enter
AltGr - PgDn
PgDn - Right Menu
PgUp - Numpad Slash
Home - Pause
End - Left Super
Delete - nowhere
Left super - nowhere
Menu - nowhere

The rest seems to be correctly mapped.

I have the exact same problem with Hardy as server and Intrepid as client.

The problem started when I upgraded from Hardy to Intrepid on the client.
When I used Hardy on the client, everything worked as expected.

---

### Post by TheFinePrint on 2008-10-27
My initial post was with the same setup; Intrepid as the client, and hardy as the server.

I just tried with WinXP as the client and it works as expected, so apparently something in intrepid breaks the client.

---

### Post by muken on 2008-10-28
> **TheFinePrint said:**
> My initial post was with the same setup; Intrepid as the client, and hardy as the server.

I just tried with WinXP as the client and it works as expected, so apparently something in intrepid breaks the client.

I found a bug report ([255008]("https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008")) on launchpad. It seems like somthing regarding the keymapping has changed in Intrepid, however this seems also to affect NX.

I'm not sure where to go from here though.

---

### Post by PeteJ on 2008-10-29
Hi all,

I had a gutsy thinkpad t21 laptop nx client connecting to a gutsy plain wrap freenx server working fine. Upgraded to Intrepid this morning and got the broken nav key problem in the nx session (up arrow opened Take screenshot and the other nav keys were borken too).

After reading tons, having no clue, flailing around, on both client and server I did System, Preferences, Keyboard, Layouts, "Evdev-managed keyboard" or similar, and then in the nx session, on the server, I did System, Preference, Keyboard shortcuts, Desktop, Take a screenshot. It was "Print", I pressed "Ctrl+PrtSc", it changed to "Ctrl+Print", and now ALL the nav keys work fine.

No rebooting, no logging out, no nothin'.

Phew.

Hope that helps some other folks.

Enjoy,
Pete

---

### Post by TheFinePrint on 2008-10-30
Excellent.  Works for me too.

---

### Post by skibrianski on 2008-11-01
+1 thanks :-D

---

### Post by dwalker109 on 2008-11-23
Thanks very much Petej, works for me too :)

---

### Post by sles on 2008-11-24
> **PeteJ said:**
> Hi all,
I did System, Preferences, Keyboard, Layouts, "Evdev-managed keyboard" 


Hello!

Could you tell me where is this "Evdev-managed keyboard" ?
I can't find it :-(

---

### Post by sles on 2008-11-24
Now it doesn't call snapshot, but arrow keys doesn't work in nx session :-(

---

### Post by albinootje on 2008-12-26
Weeks ago I ran into the same problem after starting to use Ubuntu Intrepid on my desktop.
I was using a FreeNX-server on CentOS 5.x, but by coincidence I was also testing a FreeNX-server with Ubuntu Intrepid.
In the Ubuntu FreeNX-server desktop I could change the keyboard to evdev, and on my own desktop too, and eventually it worked. (And I gave up the CentOS one, because there I could not fix it :(

But.. yesterday night I removed all of my dot gnome files and all other dot files for my user (except .profile and .bash* files) on the Intrepid FreeNX server to test OpenBox and ... the same keyboard problems happened :(

This page claims that there's a released fix :
[https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008](https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008)
but I didn't see any xorg updates for Intrepid, nor did the problem get fixed for my situation.
Am I missing something ?

---

### Post by bioborg on 2009-01-02
For me, Intrepid Client and Server, on the SERVER ONLY (within an NX session), I did: System, Preferences, Keyboard, Layouts, "Evdev-managed keyboard"

And that took care of the arrow keys.  They now work in an NX session.

---

### Post by joske on 2009-01-09
For me, the server is still running dapper, client intrepid. On the client machine, I set the keyboard settings to evdev-managed, this entry does not exist in dapper, so I can't set it on the server. It's not working, the printscreen key sends delete, arrow up sends print screen... How can I fix this?

---

### Post by albinootje on 2009-01-09
> **joske said:**
> For me, the server is still running dapper, client intrepid. On the client machine, I set the keyboard settings to evdev-managed, this entry does not exist in dapper, so I can't set it on the server. It's not working, the printscreen key sends delete, arrow up sends print screen... How can I fix this?

I've read several things about this annoying problem (I still haven't fixed it  properly), this might give you a start :
[https://bugs.launchpad.net/freenx-server/+bug/289918](https://bugs.launchpad.net/freenx-server/+bug/289918)

My vague impression is that using a custom xmodmap file can solve this.
[http://ubuntuforums.org/showthread.php?t=945199](http://ubuntuforums.org/showthread.php?t=945199)

---

### Post by joske on 2009-01-09
upgrading the NX server to 3.3.0 fixes this for me.

---

### Post by Anthon berg on 2009-02-12
Thanks!

---

### Post by swatkins on 2009-02-17
To fix this bug, on the server type:

  apt-get install xkb-data

then type:

  setxkbmap

(or restart nx)

The file /usr/share/X11/xkb/rules/xorg is the file that was needed.

This could be fixed with a dependency in one of the nx packages.

---

### Post by anystupidname on 2009-06-12
I'm sorry to report that neither selecting "Evdev-managed keyboard" layout nor reinstalling the xkb-date package helped with this problem.

---

### Post by chris_jones32 on 2009-08-26
Just adding a +1 to joske's last post: 

Upgrading the nxserver packages to 3.3.x fixed this issue for me.

---

### Post by binary.koala on 2009-09-02
> **PeteJ said:**
> 
After reading tons, having no clue, flailing around, on both client and server I did System, Preferences, Keyboard, Layouts, "Evdev-managed keyboard" or similar, and then in the nx session, 

cheers mate, doing it only on the server worked for me!

thanks again

---

