---
title: "UltraVNC Listen Mode"
date: 2008-09-18
forum: General Help
---

### Post by Hackmodford on 2008-09-18
Can I get UltraVNC and set it to listen mode?

I'm working at a bussiness where the customer will use a simple program to connect their computer to mine. If I have Listen mode running when they click I get a message asking if I want to connect. Can I do the same thing in Ubuntu?

---

### Post by HermanAB on 2008-09-18
I use the '-l' switch with Tight VNC for reverse connections.  Dunno about Ultra VNC.

You got to test it between two machines first.  (The one machine can be a virtual machine!).

---

### Post by Hackmodford on 2008-09-18
> **HermanAB said:**
> I use the '-l' switch with Tight VNC for reverse connections.  Dunno about Ultra VNC.

You got to test it between two machines first.  (The one machine can be a virtual machine!).

what is the '-l' switch?

---

### Post by lovinglinux on 2008-09-18
I know that Ultr@VNC viewer works with Wine, so maybe you could try installing Ultr@VNC server on your machine so he can connect to you, but I don't know the security implications of running this with Wine.

---

### Post by Hackmodford on 2008-09-18
Okay that sounds like an idea. But they don't make the same program for linux? I thought VNC was cross platform. 

If I do that and use listening mode will it stay running?

---

### Post by lovinglinux on 2008-09-18
> **Hackmodford said:**
> Okay that sounds like an idea. But they don't make the same program for linux? I thought VNC was cross platform. 

If I do that and use listening mode will it stay running?

I guess so. You could try any VNC Linux version, since they will probably talk to each other. For example, I'm currently using the default Remote Desktop Viewer on the Ubuntu machine to control a Windows machine running Ultr@VNC server. I never tried to other way.

---

