---
title: "Strange issue - Cant export display from Fedora"
date: 2008-10-20
forum: General Help
---

### Post by uzee007 on 2008-10-20
Hi Guys,
New to Ubuntu but not new to Unix. I have a strange probem with setting my display back, can anyone pls help/advice?
Here's the scenario:
I have this local machine (machine1) running Ubuntu 7.10 behind a router. On the router I have opened up this machine's IP in the DMZ section to be able to be visible to the world.
I have a remote machine (machine2) running fedora core 8 that I ssh into. The remote machine is also behind a router but similarly the DMZ for that IP is enabled.I can ssh into the machine no problem but cant export the DISPLAY back to my local machine.
Here's what I tried:
On remote machine: 
# export DISPLAY=<my_local_IP_visible_to_world>:0.0<my_local_IP_visible_to_world>:0.0
But still when I do xhost + it gives error "can't open display" same error if I try xterm or xclock.

On local machine:
# DISPLAY=<my_local_IP_visible_to_world>:0.0

When I ssh, I use "ssh -X <IP_Address>" and dont get an error, the X11 forwarding is enabled in the sshd config file on the remote host.
Nothing in /var/log/messages.

Why is this not working ???
Please help......

Thanks
uzee

---

### Post by uzee007 on 2008-10-20
Hello everyone.....
Any suggestions please ????
Please tell me if this belongs to a different forum so I can post there maybe?

Thanks

---

### Post by bodhi.zazen on 2008-10-20
Make sure X forwarding is enabled in /etc/ssh/sshc_config (on Fedora) and ssh_config (in Ubuntu).

Then you should just 

ssh -X use@ip

No need to set the DISPLAY (ssh will do this automagically).

Then try forwarding X applications (xeyes).

The other thought, do you have X installed on the server ?

---

### Post by netstv on 2008-10-20
Ok.. try this...

Menu:  System->Administration->Login Window

Then go to the Security Tab

Turn off "Deny TCP Connections to XServer"

I think Fedora has the same thing.  There is some wierd connection thing like that there as well.

-stv

---

### Post by uzee007 on 2008-10-21
Thanks guys, but stil no luck.
_**bodhi.zazen:**_ I have enabled all x related stuff on both local and remote machines, here are my ssh files without comments:

_On remote (Fedora)_
I have ssh_config and sshd_config in /etc/ssh

[root@localhost xinit]# grep -v ^# /etc/ssh/ssh_config
ForwardAgent yes
ForwardX11 yes
Host *
        GSSAPIAuthentication yes
        ForwardX11Trusted yes
        SendEnv LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES 
        SendEnv LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT 
        SendEnv LC_IDENTIFICATION LC_ALL
[root@localhost xinit]# 
[root@localhost xinit]# grep -v ^# /etc/ssh/sshd_config
Protocol 2
SyslogFacility AUTHPRIV
PasswordAuthentication yes
ChallengeResponseAuthentication no

GSSAPIAuthentication yes
GSSAPICleanupCredentials yes

AcceptEnv LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES 
AcceptEnv LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT 
AcceptEnv LC_IDENTIFICATION LC_ALL
AllowTcpForwarding yes
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes

Subsystem       sftp    /usr/libexec/openssh/sftp-server
[root@localhost xinit]# 

_On local machine (ubuntu)_
I only have ssh_config in /etc/ssh
root@desktop:~# grep -v ^# /etc/ssh/ssh_config
Host *
ForwardAgent yes
ForwardX11 yes
ForwardX11Trusted yes
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
root@desktop:~# 

_**netstv: **_
I have turned off the "Deny TCP connections to Xserver" on local machine, on the remote machine I dont know how as I login via ssh, don't see a desktop.

This is driving me crazy...... I would really really appreciate your help/advice.
thanks
uzee

---

### Post by unutbu on 2008-10-21
Try using the -Y flag:
```

ssh -Y <IP_Address>
xclock
```

If that does not work, check that your /etc/gdm/gdm.conf has this line:
```

DisallowTCP=false
```

See [http://linux.derkeiler.com/Mailing-Lists/Fedora/2005-07/0194.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2005-07/0194.html)

I'm not quite sure if you need this on the local machine (where you type ssh -Y) or the remote machine (running sshd). If you figure that out, please let me know.

---

### Post by uzee007 on 2008-10-21
Hi Ubuntu,
Yes I did try that already last night, ssh -Y does not work either and same for the /etc/gdm/custom.conf file (I think starting in FC8 they replaced gdm.conf with custom.conf) I added the DisallowTCP=false in the file in the [security] section, still no luck. I actually added it to both the local(ssh client) and remote (ssh server) machines.
Could it have anything to do with the fact that both machines are behind a router .... ?

---

### Post by bodhi.zazen on 2008-10-21
Try connecting with -vvv

ssh -vvv user@server

Is X installed on the server ?

What happens when you try xeyes ?

---

