---
title: "Proprietary AMD driver not working/AMD Radeon HD 6450/AMD64 Ubuntu 12.10"
date: 2012-11-05
forum: Hardware
---

### Post by eestet75 on 2012-11-05
I'm having some trouble installing the proprietary drivers for the AMD HD 6450.

I used this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)


But they haven't been successfully installed. Because when I type fglrxinfo into Terminal, it just returns:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

I even tried disabling fast TLS.
BTW It does not work, if I try to install it from software sources.
Can anyone help me?

---

### Post by 2F4U on 2012-11-05
> BTW It does not work, if I try to install it from software sources.

What is the problem when you install from the official repo? Your card should be supported by the proprietary driver that comes from the Ubuntu repositories, and I guess that would be the recommended way to install the drivers.
Do you have the same problem as in this post when installing from the official repositories?

[http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10](http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10)

---

### Post by eestet75 on 2012-11-05
> **2F4U said:**
> What is the problem when you install from the official repo? Your card should be supported by the proprietary driver that comes from the Ubuntu repositories, and I guess that would be the recommended way to install the drivers.
Do you have the same problem as in this post when installing from the official repositories?

[http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10](http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10)

I don't know if it's the same error code, but it didn't work either. Exactly the same thing happened.
Yes it's the same thing, except I have not two graphic cards and it doesn't say I'm in low graphics mode, but that may just be my monitor.

---

### Post by 2F4U on 2012-11-05
So if its the same thing, did you already try the workarounds provided in that post?

---

### Post by eestet75 on 2012-11-05
> **2F4U said:**
> So if its the same thing, did you already try the workarounds provided in that post?

I'll try to do the first one, but it requires me to reinstall. So I'll come back with results in a bit.

---

### Post by eestet75 on 2012-11-05
Works now! First answer worked. Thanks for all your help!

---

### Post by mmacmu1 on 2012-12-04
Hi,

I have a Radeon HD 6450 card and upgraded to 12.10 to have the same problems you described after installing Catalyst Control: no Unity/launcher, only the cursor displayed and the desktop at a strange resolution.

Could you please tell how you fixed it? I know you referenced the first post in [this thread]("http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10"), but the post that is currently first does not seem to have any useful directions...

Thanks in advance.

---

