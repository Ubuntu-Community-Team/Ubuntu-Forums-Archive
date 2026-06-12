---
title: "Guest session broken"
date: 2008-11-08
forum: General Help
---

### Post by jordon on 2008-11-08
I just upgraded to 8.10 with the new Fast User Switch Applet. The guest session option is there, but when I try to click it, the screen goes black and becomes locked; when I move the mouse, the box prompting me for my password appears. If I press Cancel, the screen goes white until I move the mouse and am prompted for my password again. Once I enter my password, I can get back to my session.

The same thing happens when I run /usr/share/gdm/guest-session/guest-session-launch directly. It returns the result "OK :20".

---

### Post by louieb on 2008-11-08
May be some bugs in the guest account to work out. 
1st time I clicked on it the screen went  blank  and finally returned me to the original session. So I clicked on it again just to see what would happen.  

It worked the 2nd time opened a new session as the guest user. go figure.

---

### Post by jordon on 2008-11-08
> **louieb said:**
> May be some bugs in the guest account to work out.

I guess you're right. But I'm getting the same result every time.

---

### Post by etianen on 2008-11-12
I'm also getting this.  I wonder, is it anything to do with upgrading to the new release rather than starting with a clean install?

Anyway, the button is borked.

---

### Post by hkphooey on 2008-11-14
I'm having a partial success with this. When I click on the Guest item in the menu its as you describe ... I go straight to the login screen and the mouse doesn't work -- all I can do is type the password in and get back to my original session. 

HOWEVER ... when I use the command line /usr/share/gdm/guest-session/guest-session-launch , this works, and I get the Guest session. Thanks for this info. Not sure what's going on in this case ... I too am an upgrader rather than a fresh installer, so perhaps its something to do with that.

[Later ... ]
But wait, once the command line approach had worked once, it seems the button is now working OK as well. Fantastic. Maybe it just needed 'unblocking'. 

Also quite cool ... I had my music playing in my own session ... the music continued while the Guest was logged in.

---

### Post by daveletourneau on 2009-01-05
> **etianen said:**
> I'm also getting this.  I wonder, is it anything to do with upgrading to the new release rather than starting with a clean install?

Anyway, the button is borked.
I can confirm that a clean install of Intrepid gave me the same problem on 2 different systems.

I also have another issue that seems related. When I finally log in the guest session on the second attempt (always work on second time), the window manager displays basic window borders and icons instead of the human theme. It might be another symptom for the session not properly initiating. Going to check if its always the case for multiple consecutive sessions...

---

