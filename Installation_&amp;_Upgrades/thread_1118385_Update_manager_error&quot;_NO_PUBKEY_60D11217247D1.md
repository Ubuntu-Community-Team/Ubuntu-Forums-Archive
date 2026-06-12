---
title: "Update manager error:&quot; NO_PUBKEY 60D11217247D1CFF&quot;"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Morgab on 2009-04-06
Hey all, new to the forums as well as linux.

I installed Ubuntu 8.1 on my lappy, things are working great, but when I check for updates using the update manger, it downloads all 100 files info then gives me this error:

"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/tualatrix/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
"
I've tried changing my server under synaptic manager, as well as what i presumed to be requesting the key (saw some terminal commands when i googled the problem)

but anyway, there are a 100 updates im missing out on, and i think it may be causing other issues (having trouble installing gdb)

so any help on this topic would be much appreciated

thanks!

---

### Post by Partyboi2 on 2009-04-06
Hi, you need to add the keys so open a terminal (Applications>Accessories>Terminal) and add the key for the first one with:
```
gpg --keyserver keyserver.ubuntu.com --recv  60D11217247D1CFF
gpg --export --armor  60D11217247D1CFF  | sudo apt-key add -
```
then for the 2nd one do almost the same
```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -
```
then run
```
sudo apt-get update
```

---

### Post by Morgab on 2009-04-07
it seemed to work to some extent, now it downloads the package info and i get a notification saying:

"
Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
"

I click check, and it downloads package info, but again nothing happens and the notification remains.

any ideas?
thanks

---

### Post by Partyboi2 on 2009-04-07
Are you using a proxy? If you are open up Synaptic Package Manager (System>Admin>Synaptic Package Manager) and go to Settings>Pref>Network and enter the correct proxy settings.

---

### Post by Morgab on 2009-04-07
nope, no proxy

---

### Post by mike.thenes on 2011-01-22
Hi Partyboi2,

If you still visit this thread, I had the same problem - no_PUBKEY - in Kubuntu 10.10 (more specifically with the Opera repo) and your solution worked like a charm. You rock, and thanks a lot.

---

