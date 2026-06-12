---
title: "Update Problem"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2009-09-07
I am having an ongoing problem with updates both with Update Manager and using terminal entries. I have tried 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

as well as the manager. Either way I get this error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Ideas?????

Thanks,   SteveG

  16:20 hours After trying some ideas I solved the 2EBC26B60C5A2783
issue. The other one remains

---

### Post by zvacet on 2009-09-08
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 6AF0E1940624A220
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -
```

Put one line at the time and hit enter.

---

### Post by s9032g@comcast.net on 2009-09-10
Thanks. I did this several times with some variations, but no results. I still get the same message about a GPG error.

after I input your first line I get a result saying "gpg key 062a220 "Launchpad PPA FOR Tulatrix not changed" gpg total proc 1, gpg unchanged 1

When I do the second command about armor I get a lot of gobbly gook:

BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.9 (GNU/Linux)

mI0ESXTUHwEEAMtdNPmcgQcoPN3JcUcRrmdm1chJSmX6gj28OamOgE3Nxp3XgkDd
g/vLFPv6Tk8zIMxQnvuSpuG1YGp3x8atcKlQAlEHncAo27Vlio6pk8jG+qipDBKq
7X7FyXE6X9Peg/k7t7eXMLwH6ZJFN6IEmvPRTsiiQEd/dXRRuIRhPHirABEBAAG0
G0xhdW5jaHBhZCBQUEEgZm9yIFR1YWxhdHJpWIi2BBMBAgAgBQJJdNQfAhsDBgsJ
CAcDAgQVAggDBBYCAwECHgECF4AACgkQavDhlAYkoiC8mAQAmaxr4Kw/R2WZKde7
MfbTPy7O9YoL/NQeThYGwxX6ICVr0IZUj9nxFQ/vtmhZ59p53bpdR8jpPXjdDwjZ
IIlxTf72Fky6Ri3/zsC4YRD6idS4c4L50dTy74W6IabCt8GQLtJy5YASlEp5OGwR
NptRSFxVE59LuOPRo2kvLIAa0Dc=
=3itC
-----END PGP PUBLIC KEY BLOCK-----

If I take all or part of the above and enter it as part of your last command (maybe wrong to do this??) there is no result worth mentioning.

It is very possible that I am not understanding things here.

---

### Post by drs305 on 2009-09-10
Try running this to import the keys:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0624A220  0C5A2783

```

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by s9032g@comcast.net on 2009-09-10
Thanks drs305. I don't know where you got the 0C5A2783 part but the whole thing worked. The error message is gone. The result was that the update reloaded Firefox and supporting files. I don't understand why, but I am happy with the result.

Enjoying the Ubuntu experience.  SteveG

---

### Post by drs305 on 2009-09-10
> **s9032g@comcast.net said:**
> Thanks drs305. I don't know where you got the 0C5A2783 part but the whole thing worked. 

Steve,
Just for background...  The error messages you were receiving actually were telling you the problem:
> 
The following signatures couldn't be verified [COLOR="DarkRed"]because the public key is not available[/COLOR]: NO_PUBKEY 6AF0E1940624A220
The following signatures couldn't be verified [COLOR="DarkRed"]because the public key is not available[/COLOR]: NO_PUBKEY 2EBC26B60C5A2783

To resolve this, you import the public key cited in the error message:
> 
NO_PUBKEY [COLOR="DarkRed"]6AF0E1940**624A220**[/COLOR]
NO_PUBKEY [COLOR="DarkRed"]2EBC26B6**0C5A2783**[/COLOR]


The command I gave referenced the code and requested the public key be imported into your machine. The command would have accepted the entire code (e.g. 2EBC26B60C5A2783 ) but only the last 8 alphanumeric characters are required (e.g. 0C5A2783 ).


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by hubertofliege on 2009-09-10
I tried running the code above, but substituting in the key numbers for all my keyless sources, and it seems to have worked for those, however a few of them were different.  These are the error messages remaining: 

"
GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead."

What does all* this* mean?

---

### Post by drs305 on 2009-09-10
hubertofliege,

For the public key, you have to run the key specific for the error message. Each repository will generate a different public key to import. In this case the command to run would be:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6DFBCBAE
```
This command imported the key for me.

For the other errors, you may have something wrong in the sources.list or in the associated file in /etc/apt/sources.list.d
Post the contents of the list with the mysql references and we can look at it.

---

### Post by hubertofliege on 2009-09-13
That command I've already run, and it worked for all of the missing Public Keys.  What I have left though is one Bad Signature and two files that won't open.  I don't know what to do about these three.

---

### Post by drs305 on 2009-09-13
> **hubertofliege said:**
> That command I've already run, and it worked for all of the missing Public Keys.  What I have left though is one Bad Signature and two files that won't open.  I don't know what to do about these three.

For the bad signature, you can try opening Synaptic > Settings > Repositories: Authentication. Look for entries that reference the ones in the BADSIG error message and remove them. The next time you attempt to access those repositories you will be asked to import the key again.

You will have to post the error message for the "two files" that won't open or open your sources.list or *.list file in /etc/apt/sources.list.d and fix or comment out ( # ) the offending entry.

---

