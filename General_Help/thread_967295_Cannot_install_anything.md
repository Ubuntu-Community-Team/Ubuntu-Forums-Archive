---
title: "Cannot install anything"
date: 2008-11-01
forum: General Help
---

### Post by murphyj on 2008-11-01
Just installed 8.04 and it will not install anything else. Try to install mp3 support for media players and it says dpkg failed. run dpkg --configure -a to correct. Go to terminal and that does absolutely nothing. Cannot install limewire because it says can only run one package manager at a time, so it does nothing. Getting VERY frustrated.

---

### Post by ugm6hr on 2008-11-01
```
sudo dpkg --configure -a
```

---

### Post by oldos2er on 2008-11-01
Do you have a working internet connection? Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by murphyj on 2008-11-02
Thank you, ugm6hr. That fixed it. Got both installed. Oldos2er, I have no idea what you're talking about, or how to comply with your request.

---

### Post by ugm6hr on 2008-11-02
> **murphyj said:**
> Thank you, ugm6hr. That fixed it. Got both installed. Oldos2er, I have no idea what you're talking about, or how to comply with your request.

The "man" command explains everything (i.e. gives you a manual):
```
man dpkg
```
gives a full manual - including:
```
             --configure package...|-a|--pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.


```

Sudo is required to run dpkg commands: [http://www.psychocats.net/ubuntu/security#sudoisnotroot](http://www.psychocats.net/ubuntu/security#sudoisnotroot)

So - basically, something untoward happened during the original installation which interrupted the process - this command just tries to install the same packages again.  Unfortunately, this can only be done from the command line - but at least Synaptic tells you what to type in (it assumes you understand the sudo security model)!

Oldos2er was asking you to do the following, and then tell us what it said (this is not necessary - but is useful to understand future advice from people):
```
cat /etc/apt/sources.list
```

---

