---
title: "Can't connect via VNC"
date: 2008-08-11
forum: General Help
---

### Post by letubenaiah on 2008-08-11
I'm having some problems connecting to my Ubuntu Hardy machine using VNC.  I can connect my computer to itself via ```
vncviewer localIP:0
``` and it all works fine.  But if I try to connect from a windows computer on the network using realVPN I get this error "unable to connect to host: Connection reset by peer (10054)"  I've made sure that ports 5800 and 5900 are both open using nmap.

Thanks for any help!

---

### Post by starcannon on 2008-08-11
I'd recommend tightVNC its available for windows and linux(Ubuntu Synaptic Package Manager), so far its given me the least problems, of course depending on your variables your mileage may vary.

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

GL

---

### Post by letubenaiah on 2008-08-11
> **starcannon said:**
> I'd recommend tightVNC its available for windows and linux(Ubuntu Synaptic Package Manager), so far its given me the least problems, of course depending on your variables your mileage may vary.

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

GL

I went into the package manager and uninstalled all the other vnc clients expect for tightVNC (tightvncserver).  I ran vncserver and it gave me the "New 'X' desktop ..." and it all seemed fine on that end.  But I'm still getting the connection rest by peer error or a connection refused error when I try to connect to it.

---

### Post by starcannon on 2008-08-12
Okay let me make sure I'm on the same page:

You can vnc from windows into linux on other computers on your network:

```

              _________ Linux 1
             /_____________________Linux 2  
            /________________________________Linux 3
           /
Windows--->
           \____________________Linux 4 (rejects connection) 



```

Is this a good picture of whats happening?

If so I'm guessing Linux 4 has a firewall issue.

---

### Post by letubenaiah on 2008-08-12
Thats not quite whats happening.  Here it is:

```
   
                                     _________ Windows 1
                                    /_________________Windows 2  
                                   /
                                  /
(Rejecting connections) Linux --->
                                  \____________________Mac 1


```

Linux machine can access both windows computers and the mac computer, but when either of the windows computers or the mac tries to access the Linux machine they get rejected.

---

