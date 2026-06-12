---
title: "W: GPG error: http://ppa.launchpad.net intrepid Release"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2009-04-10
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF 

I have had the following error after running updates on two separate PCs.  Both started with clean hard drive and Ubuntu 8.10 live cd.

Launchpad was added to sources.list to get OpenOffice.

One person told me I had the wrong stuff in my home directory, but I didn't put it there and I am only user of the PCs

How do I get a verified public key?

John

---

### Post by zvacet on 2009-04-11
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 60D11217247D1CFF
gpg --export --armor  60D11217247D1CFF | sudo apt-key add -
```

---

### Post by cigtoxdoc on 2009-04-12
Thank you very much for the help.


The fix was perfect.

JHL

---

### Post by eferrara on 2009-05-02
Hello:

I have just installed 9.04 and get the following error when I do an update request:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60487016493B3065
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

I tried the fix noted in the above thread and it did not help.  Any help would be appreciated. Thanks.

---

### Post by zvacet on 2009-05-02
Put one line at the time in terminal.It should work for you too.

---

### Post by Old_Grey_Wolf on 2009-05-02
Substitute the keys you need like so
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 60487016493B3065
gpg --export --armor  60487016493B3065 | sudo apt-key add -
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 9423A34CCA967634
gpg --export --armor  9423A34CCA967634 | sudo apt-key add -
```

---

### Post by sag on 2009-05-03
Hi,
This fix worked for me after my installation of virtualbox stopped working. I ran the 'Computer Janitor' app. in Administration, and it suggested the virtualbox.deb file was no longer needed, but apparently it is!
sag

---

### Post by zvacet on 2009-05-03
I should give general command 

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
```


Replace **KEY** with number.

---

### Post by RazorV on 2009-12-10
> **zvacet said:**
> ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 60D11217247D1CFF
gpg --export --armor  60D11217247D1CFF | sudo apt-key add -
```


Just wanted to say thanks for this bit of info!  It fixed my problem!  Cheers!

Greg

---

