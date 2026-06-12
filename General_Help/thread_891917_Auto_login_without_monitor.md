---
title: "Auto login without monitor"
date: 2008-08-16
forum: General Help
---

### Post by jaggerlink on 2008-08-16
I am setting up a game server in my basement. I want it to be able to auto login without a monitor, which I can not find out how to be able to do. When I have a monitor plugged it, it works correctly (skips the ubuntu login screen, goes straight to my desktop and runs a .sh file.), but when there is not monitor attached, it doesn't login. When I attach a monitor, it sits at the login screen.

I need to be able to control the computer after it is started, which I had planned on doing with VNC, but it seems like ssh might be my only option. The only problem is that I need wine to run, and I don't know if it will work without a gui (even though the program I have running is a command-line program.)

Can someone please help me?

---

### Post by jaggerlink on 2008-08-17
Can anyone help?

---

### Post by Roasted on 2008-08-17
No idea on how the auto login works, but if all else fails, can't you just rdesktop into it and login, then close out quick?

---

### Post by sameerds on 2008-08-17
> **jaggerlink said:**
> I am setting up a game server in my basement. I want it to be able to auto login without a monitor, which I can not find out how to be able to do. When I have a monitor plugged it, it works correctly (skips the ubuntu login screen, goes straight to my desktop and runs a .sh file.), but when there is not monitor attached, it doesn't login. When I attach a monitor, it sits at the login screen.

I don't claim to be an expert, but I am very curious about this. I don't see a reason why authentication should be affected by the presence or absence of a monitor. How have you configured the PC to autologin?

Also, why do you need to login to be able to run the script? You could simply add it to your rc-scripts so that the script is executed when the machine finishes booting. The rc-scripts can even run your script with your id if you specify.

> **jaggerlink said:**
> I need to be able to control the computer after it is started, which I had planned on doing with VNC, but it seems like ssh might be my only option. The only problem is that I need wine to run, and I don't know if it will work without a gui (even though the program I have running is a command-line program.)

Can someone please help me?

What you are saying here is confusing. What is it exactly that you want to do?

---

### Post by jaggerlink on 2008-08-18
> **sameerds said:**
> I don't claim to be an expert, but I am very curious about this. I don't see a reason why authentication should be affected by the presence or absence of a monitor. How have you configured the PC to autologin?

System -> Administration -> Login Window

> **sameerds said:**
> Also, why do you need to login to be able to run the script? You could simply add it to your rc-scripts so that the script is executed when the machine finishes booting. The rc-scripts can even run your script with your id if you specify.

Would I be able to use vnc without logging in?

> **sameerds said:**
> What you are saying here is confusing. What is it exactly that you want to do?

I want to have remote control over the computer after it is booted (which I was hoping to do using vnc)

Thanks again.

---

### Post by cariboo on 2008-08-18
I use my server all the time without logging in. It always just sits there at the login prompt. Can you log in with ssh? Here is a link to a ssh howto, including how to x-forwarding for graphical programs:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Jim

---

### Post by sameerds on 2008-08-18
> **jaggerlink said:**
> System -> Administration -> Login Window

OK. That basically runs gdmsetup, which is a tool to configure the login screen. It is possible that when gdm starts the X server, the system probes for the monitor settings. Since there is no monitor to probe, gdm might decide to abort, and try again when a monitor is connected. You should check these logs under /var/log to see what could be wrong: gdm, Xorg and auth.log. If this is because of monitor autoconfigs, you could configure X to use a specific monitor so that it does not probe, but I am just guessing here.

> **jaggerlink said:**
> Would I be able to use vnc without logging in?

I don't know. I have never used VNC. From what I have heard, VNC is used to export a running desktop. Maybe there is a way to run it at boot time, so that the login window itself appears at the client machine. There's probably a HOWTO out there on some VNC support forum for this.

> **jaggerlink said:**
> I want to have remote control over the computer after it is booted (which I was hoping to do using vnc)

You can always use ssh, or even remote logins through gdm (the same tool that you had used to enable autologin has a tab called "Remote"). But if the client is a windows PC, that can be quite a pain.

---

### Post by jaggerlink on 2008-08-18
> **sameerds said:**
> OK. That basically runs gdmsetup, which is a tool to configure the login screen. It is possible that when gdm starts the X server, the system probes for the monitor settings. Since there is no monitor to probe, gdm might decide to abort, and try again when a monitor is connected. You should check these logs under /var/log to see what could be wrong: gdm, Xorg and auth.log. If this is because of monitor autoconfigs, you could configure X to use a specific monitor so that it does not probe, but I am just guessing here.

You were right, the logs confirm that it fails due to the lack of a monitor.

> **sameerds said:**
> I don't know. I have never used VNC. From what I have heard, VNC is used to export a running desktop. Maybe there is a way to run it at boot time, so that the login window itself appears at the client machine. There's probably a HOWTO out there on some VNC support forum for this.

> **sameerds said:**
> You can always use ssh, or even remote logins through gdm (the same tool that you had used to enable autologin has a tab called "Remote"). But if the client is a windows PC, that can be quite a pain.

While I can connect with ssh, and it would normally be a perfect option, the program I want to run requires a gui apparently, even though it runs in a command prompt (through Wine)

When I try to run the script from ssh:

```
Aaron@basement-server:~$ source Desktop/startserver.sh
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 2
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
wine: Unhandled page fault on write access to 0x6d82b9aa at address 0x7ee5ca25 (thread 001a), starting debugger...
Unhandled exception: page fault on write access to 0x6d82b9aa in 32-bit code (0x7ee5ca25).
```It then gives me a register dump.

I guess I need to go find out if I can run the program without a gui.

EDIT: I managed to get the program to run from ssh via xvfb. Only problem now is that because there is no window for the server, I can not see what is happening. I cant do anything with it. I need to find a way to have a gui without a monitor so that I can access the server via vnc.

It's never easy, is it?

---

