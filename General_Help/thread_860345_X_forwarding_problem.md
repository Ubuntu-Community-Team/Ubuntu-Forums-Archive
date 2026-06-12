---
title: "X forwarding problem?"
date: 2008-07-15
forum: General Help
---

### Post by eekrazyk on 2008-07-15
I'm having a problem with X forwarding that I can't seem to figure out.

I'm running Kubuntu 8.04.  I am able to run apps from a linux cluster here at work, but when I try to run an app from a Sun box it dies with this error:

```

// cannot connect to Xserver '10.33.49.239:0'
// X server is not running
// Cannot initialize device driver.
//  Error: Connection to hardware type X11dd failed (from: Core/VDD/vdd 08)

```

I'm using the -X option with ssh.

```

> printenv | grep -i display
DISPLAY=10.33.49.239:0
UI_DISPLAY=X11dd

```

I'm not sure what the UI_DISPLAY variable is... but the error above mentions X11dd, too.  ??


The funny thing is I can ssh to our linux cluster and run apps without any errors.  When I try to run stuff from the Sun box, I get back errors indicating I have a problem with X on my end... ??

Anyone have any ideas?

---

### Post by tramir on 2008-07-15
I don't know if this will help solve the problem, but I had some problems with X forwarding in the past too (not your error message, though). What I read was that a "better" way to forward X is to use the -Y switch. You might get a warning about auth data, but you can safely ignore it. You can try this and see if it makes a difference.

---

### Post by eekrazyk on 2008-07-15
> **tramir said:**
> I don't know if this will help solve the problem, but I had some problems with X forwarding in the past too (not your error message, though). What I read was that a "better" way to forward X is to use the -Y switch. You might get a warning about auth data, but you can safely ignore it. You can try this and see if it makes a difference.

Oops.  I forgot to mention that I have tried using the -Y option and still receive the same error.

---

### Post by eekrazyk on 2008-07-15
Doh.  I feel like a fool.

I have my .cshrc set up for both linux and Sun boxes...

```

if ($OS_NAME == "Linux") then
    if (`printenv REMOTEHOST` != "" && `printenv SSH_CLIENT` == "") then
        setenv DISPLAY `echo $REMOTEHOST`:0
    endif

.......

if ($OS_NAME == "SunOS") then
    if (`printenv REMOTEHOST` != "" ) then
        setenv DISPLAY $REMOTEHOST":0"
    endif

```

See the problem?  My DISPLAY variable should have been set to something like 'localhost:10.0', but instead was set to my workstation IP.

All is fixed now.  I added the '&& `printenv SSH_CLIENT` == ""' part to the SunOS part.

Thanks for the replies.

---

### Post by timcredible on 2008-07-15
is there a firewall between the 2 machines?  if not, just run Xnest to access the other unix/linux machine, it's much easier:

Xnest :30 -query <remote host>

Xnest is in the repos.  you may need to turn on remote access of xdm on the remote machine, more info on that in my sig.

if the above doesn't help, the -X is what you should be able to use, just make sure the -display is correct when running the app.

---

