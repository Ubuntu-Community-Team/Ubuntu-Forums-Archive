---
title: "SSH Server + Encrypted channel"
date: 2005-11-22
forum: General Help
---

### Post by DADDA on 2005-11-22
Do enyone now a good guide or can someone help me install a SSH Server?
I also needs som help whit configuring its security...

Is it possible to make a encrypted channel? So I can send files and make a VPN between my home computer and my computer at work? 

So on my brakes that I can use MSN Messenger, ICQ, AIM, IRC and some other useful thinks

---

### Post by suRoot on 2005-11-22
Open Synaptic (System -> Administration -> Synaptic) & search for ssh.  From the results, click SSH which will also prompt you to install open-ssh-server.  Click apply & ssh will be installed.

Just to make sure the keys are generated, run:

```
sudo /etc/init.d/ssh restart
```

Then from the console you can type

```
ssh -l <username> 127.0.0.1
```

Which will output the following:

```
$ ssh -l foo 127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is ac:be:6d:5e:a6:10:33:f6:6a:08:33:57:1a:33:69:3e.
Are you sure you want to continue connecting (yes/no)? yes
```

If you get that far the server is up & running & you're ready to roll.

If you have a firewall, you'll need to forward port 22 from the external interface to your Ubuntu box to allow SSH connections.

A good explanation of SSH tunneling can be found here:
[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html]("http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html")

---

