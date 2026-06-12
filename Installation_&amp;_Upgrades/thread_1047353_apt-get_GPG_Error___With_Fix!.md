---
title: "apt-get: GPG Error:   With Fix!"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by sysadmn62 on 2009-01-22
During a recent 'apt-get update', I got the following confusing error message:

 > W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0

I'm not sure why this just began happening, but here's the scoop.  Developers sign their releases in order to prevent others from tampering with the contents.  In order for apt-get to trust a package, it needs the developer's public key to check that signature.

**Here's how to add a missing key:**

If you are in a root shell, you can omit the *sudo* in each of these commands.

Add the key to your system's keyring.  The key is given in the error message - in this example, 28A8205077558DD0.  There are two ways to do this.  Developers can provide the key for download on their website, or put the key on a well-known keyserver.  When the repository is added, the instructions usually include the steps needed to add the key.  If you know which package is causing the problem, check the download page for that package.  For example, [mediabuntu]("https://help.ubuntu.com/community/Medibuntu") has a dedicated package for it's keyring:

```

# sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Google offers its' [key]("http://www.google.com/linuxrepositories/aboutkey.html") for download:

```

# *sudo *wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | *sudo *apt-key add -
*sudo *apt-get update

``` 


If that fails, try using the keyserver at subkeys.pgp.net:


```
 
# *sudo* gpg --keyserver hkp://subkeys.pgp.net --recv-keys 28A8205077558DD0
getting 28A8205077558DD0 key
gpg: requesting key 77558DD0 from hkp server subkeys.pgp.net
gpg: key 77558DD0: public key "Launchpad PPA for GNOME Do Core Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
***Warning!***  You don't want to add keys for just anyone.  You must check and make sure that the title of the key (e.g. "Launchpad PPA for GNOME Do Core Team") corresponds to a repository you're actually using.  Unfortunately, apt-get's error message is not helpful - it only shows the domain ([http://ppa.launchpad.net](http://ppa.launchpad.net)) and not the full url for the failing package.

If you trust the key, add it to apt-get:
```

 *sudo* gpg --export --armor 28A8205077558DD0 |  *sudo* apt-key add -
OK

```


Please let me know of any comments or corrections by replying to this thread.

---

### Post by Paresh on 2009-02-02
How do I know which package the key belongs to?

I get errors on two keys

```
W: GPG error: http://ppa.launchpad.net intrepid Release: ... NO_PUBKEY 
```

The two keys are ```
60D11217247D1CFF
``` and ```
28A8205077558DD0
```

Both say Intrepid Release, so which packages are causing the problem?

---

### Post by Seq on 2009-02-02
> **Paresh said:**
> How do I know which package the key belongs to?

I get errors on two keys

```
W: GPG error: http://ppa.launchpad.net intrepid Release: ... NO_PUBKEY 
```

The two keys are ```
60D11217247D1CFF
``` and ```
28A8205077558DD0
```

Both say Intrepid Release, so which packages are causing the problem?

What PPAs do you have in use? PPAs recently became signed. There is an article in the wiki regarding [Adding a PPA to your system]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") that covers importing keys.

I am at work, so please let me know if this does not work for you. Replace they KEYID value with the key you wish to add:

**EDIT**: Removed code as it didn't work. See down three posts.

---

### Post by SamNSane on 2009-02-02
> **Seq said:**
> What PPAs do you have in use? PPAs recently became signed. There is an article in the wiki regarding [Adding a PPA to your system]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") that covers importing keys.

I am at work, so please let me know if this does not work for you. Replace they KEYID value with the key you wish to add:

```
KEYID=60D11217247D1CFF  gpg --no-default-keyring --keyring /tmp/keyring.tmp --keyserver keyserver.ubuntu.com --recv  ${KEYID} && gpg --no-default-keyring --keyring /tmp/awn.keyring --export --armor ${KEYID} | sudo apt-key add - && rm /tmp/keyring.tmp
```

I've been trying to do this all day. The problem is that, when I click on a fingerprint link, the darned browser times out. This is for three different PPA keys, not just one. So I'm wondering if there's a more-or-less "global" problem at the launchpad PPA site.

---

### Post by Seq on 2009-02-02
> **SamNSane said:**
> I've been trying to do this all day. The problem is that, when I click on a fingerprint link, the darned browser times out. This is for three different PPA keys, not just one. So I'm wondering if there's a more-or-less "global" problem at the launchpad PPA site.

I'm travelling to my LUG tonight, but I've decided to pop home quickly to confirm this command works, and to check out the keyserver (It goes to port 11371, which is blocked at my place of employment).

---

### Post by Seq on 2009-02-02
> **SamNSane said:**
> I've been trying to do this all day. The problem is that, when I click on a fingerprint link, the darned browser times out. This is for three different PPA keys, not just one. So I'm wondering if there's a more-or-less "global" problem at the launchpad PPA site.

Alright, the following works. You can replace the KEYID value with the long key that is on the PPA's info page, right where it says "This repository is signed with XYZ OpenPGP key."

```
KEYID=XYZ;  gpg --no-default-keyring --keyring /tmp/keyring.tmp --keyserver keyserver.ubuntu.com --recv  ${KEYID} && gpg --no-default-keyring --keyring /tmp/keyring.tmp --export --armor ${KEYID} | sudo apt-key add - && rm /tmp/keyring.tmp
```

If you have lots of PPAs to add, you could put this in your ~/.bashrc:
```
# Add PPA keys
function add-ppa-key
{
        APTKEYID=${1}
        gpg \
                --no-default-keyring \
                --keyring /tmp/keyring.tmp \
                --keyserver keyserver.ubuntu.com \
                --recv  ${APTKEYID}
        gpg \
                --no-default-keyring \
                --keyring /tmp/keyring.tmp \
                --export --armor ${APTKEYID} \
        | sudo apt-key add -
        rm /tmp/keyring.tmp

        SHORTAPTKEYID=`echo ${1} | sed 's/.*\(.\{8\}\)$/\1/'`
        sudo apt-key list | grep -A 1 ${SHORTAPTKEYID}
}
```

You would then call that function in the following way:

```
add-ppa-key XYZ
```

---

### Post by SamNSane on 2009-02-03
Thank you for the suggestions, **Seq**.

The problem resolved itself by yesterday evening. I even tried via a couple of different ISPs and with a couple of different systems, and saw the same timeout problem. But a repeated attempt late in the evening (east coast, US) resulted in immediate display of the pages. So I just used the GUI procedure.

---

### Post by Paresh on 2009-02-03
Thanks

That worked and the keys have now been added.

---

### Post by forger on 2009-02-06
I made a script too:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

Fixes the ppa link and adds the keys :)

---

