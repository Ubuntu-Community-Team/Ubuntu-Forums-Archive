---
title: "Possible to use different window decorations for different apps?"
date: 2008-08-20
forum: General Help
---

### Post by Endolith on 2008-08-20
Really all I want is for apps on another computer (through X11-forwarding ssh -X) to have a different color title bar, so it's easy to remember which computer the app is running on just by glancing out the corner of my eye.

I use blue for my laptop, red for my other laptop, purple for my desktop, etc.  It would be great if this color could be carried over X11 forwarding as well.

But I can imagine people wanting to use entirely different window borders for different apps, etc.

---

### Post by master.swarky on 2008-08-20
Well, I would look for a solution, knowing that you can set different window decorations for different users. Why not logging on your desktop with one user, laptop with another etc?

---

### Post by Endolith on 2008-08-20
> **master.swarky said:**
> Well, I would look for a solution, knowing that you can set different window decorations for different users. Why not logging on your desktop with one user, laptop with another etc?

Well I am logging in as another user, through ssh.  Do you mean that you can set different window decorations for different users who are logged into the same session?  I don't think that really makes sense, but I'm not sure about how logging in works.  What I want is to start Nautilus from my laptop and see a blue title bar.  Then use ```
ssh -fXC desktop nautilus
``` to run Nautilus on the desktop, but view the display on my laptop, but with the title bar -- which says "Nautilus (on desktop)" -- in purple.

I know it's possible to create windows without borders, so it seems like this might be possible somehow.

Maybe I should be asking if it's possible to forward window decorations through X.

---

### Post by master.swarky on 2008-08-20
Well, maybe it can look like that: (it's a nasty workaround, to be true :( )

Create a user called 'desktopforw' on your laptop and give him purple window decorations.
Then, log in like that:

```
sudo -u desktopforw ssh -fXC desktop nautilus
```

Not really the solution you wanted, but I think it'll work. 

Cheers :)

---

### Post by amitkher on 2008-08-20
I am logged in as the user tarzan. When I open an application as another user (jane) from my desktop session using sudo, I get the window decorations of tarzan and not jane.

So I don't see how this will solve the problem.

---

### Post by master.swarky on 2008-08-20
Strange. I remember doing like that: giving different window decorations to my regular user and root on my desktop. And it worked, so I thought here would be the same. AFAIK there was some how-to or whatever.

---

### Post by Endolith on 2008-08-20
> **master.swarky said:**
> Create a user called 'desktopforw' on your laptop and give him purple window decorations.
Then, log in like that:


I'm *always* logged in as a different user; it's a different machine.  :)  The window decorations are not forwarded, just the window itself.  It uses the window decorations of the local desktop.

---

### Post by amitkher on 2008-08-20
> **Endolith said:**
> I'm *always* logged in as a different user; it's a different machine.  :)  The window decorations are not forwarded, just the window itself.  It uses the window decorations of the local desktop.

 master.swarky  meant a different local user. You become a different user of your own machine, and then ssh to the remote machine.

This does not work for me anyway(with gnome).

---

### Post by master.swarky on 2008-08-20
Thanks, amitkher, that's what I meant:)
Anyway, it's strange it doesn't work. Maybe try starting another X session (so there will be 2 simultaneosly), log in as different local user and try?
I suppose, the reason is the GNOME is messing some things. Try it with another, possibly lighter WM - fluxbox or openbox for example.

---

### Post by Endolith on 2008-08-22
> **master.swarky said:**
> Maybe try starting another X session (so there will be 2 simultaneosly), log in as different local user and try?

How does that work?  I don't think this is really something you solve with different users.  I am wondering if it's possible to use different window decorations for different apps run by the same user on the same machine.  Surely this is possible, if we can have windows with no decorations at all.

---

