---
title: "VNC &#8211; password wont work :&lt;"
date: 2008-09-20
forum: General Help
---

### Post by syborfical on 2008-09-20
Currently using Ubuntu 7.04 

I have installed VNC4 server and it works with resumable sessions. !!! With no password. 

The only problem is, it won&#8217;t work with a _password._

I have reset my password by:
Vncpasswd /root/.vncpassword and say I type password.

When I go to my other machine or VNC on the local machine it will not accept the password. Even though it is correctl.
I have deleted changed permissions to /root/.vncpassword. 

Also I have 

Uninstalled vnc4server &#8211;purge etc. reinstalled vnc4server.

Still no luck


I have formatted twice put ubuntu 7.04 and tried 8.04 and still the same thing. 

In my Xorg.conf I have the following to get VNC to load when X (gnome starts)


Section "Module"
  Load "vnc"
EndSection


Section "Screen"
  Option "SecurityTypes" "VncAuth"
  Option "UserPasswdVerifier" "VncAuth"
  Option "PasswordFile" "/root/.vnc/passwd"
 EndSection

It works fine when I have  Option "SecurityTypes" "None".

So im pretty sure there is some issue with my VNC auth just not sure how to fix it.

Also my /etc/xinetd.d/Xvnc looks like this:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

Anyone else got any ideas? 

Cheers thank you for reading.

---

