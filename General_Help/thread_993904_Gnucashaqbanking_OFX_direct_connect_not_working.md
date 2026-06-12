---
title: "Gnucash/aqbanking OFX direct connect not working"
date: 2008-11-26
forum: General Help
---

### Post by danielsbrewer on 2008-11-26
I am having problems setting up OFX directconnect in gnucash to download my statements from my bank.  I am running ubuntu intrepid.  It should be said at the start that I found a python script on the internet which will download the OFX files, so I know the details I have got from my bank are correct, but I would like it to work within Gnucash.

Basically the problem seems to be within aqbanking the backend that does the work.  When I run the wizard and try and get a list of my accounts with the bank I get the following:
```
/usr/lib/aqbanking/plugins/20/wizards/qt3-wizard -v
3:2008/11/26 12-43-35:aqbanking(20872):qbanking.cpp:  420: No Qt translation found for your language en
3:2008/11/26 12-43-58:gwen(20872):io_tls.c: 1154: gnutls_handshake: -9 (A TLS packet with unexpected length was received.) [fatal]
3:2008/11/26 12-43-58:(null)(20872):provider.c:  659: Error exchanging getAccounts-request (-66)
3:2008/11/26 12-43-58:qt3_wizard(20872):cfgtabpageuserofx.cpp:  283: Error requesting account list
```

It appears to be a problem with gnutls, which I think is an encryption library. Any ideas on how to fix this?

Thanks

---

### Post by Jive Turkey on 2008-12-07
Can you use ofxdirectconnect (in gnucash) to DL your transactions or balance?  In previous releases I have got gc compiled to enable ofx but not Ibex yet.  I have found that my bank does not support account list download, only transactions and balances, and only from checking accounts,  not savings.  I haven't been able to get any of this to work in Intrepid yet at all.

---

### Post by danielsbrewer on 2008-12-07
I haven't managed to get gnucash/aqbanking to do anything.  The python script I got can list the accounts and I have managed to get all my accounts through it.

---

### Post by Jive Turkey on 2008-12-07
Probably one of the gnucash packages needs to be compiled by user, possibly obtained from a source other than the repos.  I think maybe libgwen or libaqbanking or libofx.  We'll get this figured out, I've managed to do it in every release since Edgy. 

I'm very pleased that the devs have put in some time to almost having a working version in the repos, it used to be worse.

---

### Post by elsaturnino on 2008-12-15
I ran into the same problem just now. I hadn't realized that Intrepid has out-of-the-box support for online banking with GnuCash. Sadly, it doesn't seem to work correctly as of now.

I previously had online banking working when I would compile it myself. If you just can't wait to have online banking, you could always try the compilation route. You can find pretty simple directions at: [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

---

### Post by danielsbrewer on 2008-12-15
If you give compiling a go, can you tell me how you get on? 

Thanks

---

