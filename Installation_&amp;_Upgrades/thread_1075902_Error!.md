---
title: "Error!"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by blackrockzig on 2009-02-20
rr [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems



How do I fix these errors?

---

### Post by fatbotgw on 2009-02-20
I'm getting the same thing.  My guess would be that the server is currently down/unavailable.  Just try it again later...

---

### Post by thnn on 2009-02-20
hmh, I'm stuck until I get a new package from there.

Is there no status page that lets us know when repository servers go down, or when they're projected to come back?

---

### Post by blackrockzig on 2009-02-20
Is there anyway to just get arid of them because everything is working fine and obviously don't need them?

---

### Post by cariboo on 2009-02-20
You  can use a different server, if you really need the package. Go to System-->Administration-->Software SOurces and click the download from dropdown and select other. Next click Select Best Server and let it check which server is best for you, once it's done click Choose Server and update the repositories.

Jim

---

### Post by blackrockzig on 2009-02-21
> **cariboo907 said:**
> You  can use a different server, if you really need the package. Go to System-->Administration-->Software SOurces and click the download from dropdown and select other. Next click Select Best Server and let it check which server is best for you, once it's done click Choose Server and update the repositories.

Jim

And if I don't want them...

---

