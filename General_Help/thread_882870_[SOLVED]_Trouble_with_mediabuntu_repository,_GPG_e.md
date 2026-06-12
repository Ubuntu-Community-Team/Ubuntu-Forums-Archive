---
title: "[SOLVED] Trouble with mediabuntu repository, GPG error"
date: 2008-08-07
forum: General Help
---

### Post by Drizzel on 2008-08-07
I'm trying to enable the mediabuntu repositories and keep getting this error.. What can I do to get the key or whatever it's wanting?

```

W: GPG error: [http://packages.mediabuntu.org](http://packages.mediabuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available. NO_PUBKEY 2EBC26B60C5A2783
```

---

### Post by Vivaldi Gloria on 2008-08-07
Try

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Drizzel on 2008-08-07
Hi thx for the reply :)

I get this now:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct


Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Some index files failed to download, they have been ignored, or old ones used instead.


My network connection is fine. Is the repository just temporarily down?

I used this for adding the repository:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free  <-- Is that correct?

---

### Post by Vivaldi Gloria on 2008-08-07
> **Drizzel said:**
> I used this for adding the repository:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free  <-- Is that correct?

The better way to install is this: Goto

[http://www.medibuntu.org/](http://www.medibuntu.org/)

and click repository howto. The commands there are as follows:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

These commands install without a problem.

---

### Post by Drizzel on 2008-08-07
I"m still getting:

Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


Is that normal?

---

### Post by Vivaldi Gloria on 2008-08-07
> **Drizzel said:**
> ... Is that normal?

Did you first remove the line you added yourself? Then run both of the commands from the medibuntu howto.

---

### Post by Drizzel on 2008-08-07
Yes, I removed it, reloaded, then ran the commands you posted from mediabuntu.

Well I have to get some sleep.. I'll check back in a bit. Thanks for your help :)

---

### Post by Vivaldi Gloria on 2008-08-07
> **Drizzel said:**
> Yes, I removed it, reloaded, then ran the commands you posted from mediabuntu.

Well I have to get some sleep.. I'll check back in a bit. Thanks for your help :)

It seems that the package list is down for the moment. Try again later.

---

### Post by Drizzel on 2008-08-07
I just tried again and I'm still getting the gpg error..

W: GPG error: [http://packages.mediabuntu.org](http://packages.mediabuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available. NO_PUBKEY 2EBC26B60C5A2783

I dont know what is going on. I used to have the mediabuntu repositories enabled, but reinstalled several weeks ago. Now I'm trying to enable them again and its just giving me errors. All the other repos work.

---

### Post by Vivaldi Gloria on 2008-08-07
OK. [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is online again. Try the two commands now.

---

### Post by pmsumner on 2008-08-07
> **Vivaldi Gloria said:**
> OK. [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is online again. Try the two commands now.

And now appears to be back down again :(

Boooooo!

---

### Post by Drizzel on 2008-08-07
Well I guess its ok now, I still got the errors when running the command. However now when I try to update via 'update manager' it doesnt give me any errors and I see the mediabuntu entry under authentication in 'software sources'. So I assume it got the key.. dunno why I still got the errors. Guess its offline again or something.. Is the mediabuntu repo normally so hit and miss?


```
Err http://packages.medibuntu.org hardy/free Packages    
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err http://packages.medibuntu.org hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err http://packages.medibuntu.org hardy/free Sources     
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err http://packages.medibuntu.org hardy/non-free Sources 
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Drizzel on 2008-08-08
So can anyone tell me if these failed files are necessary?


W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz](http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

---

### Post by kostkon on 2008-08-08
> **Drizzel said:**
> So can anyone tell me if these failed files are necessary?


W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz](http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

 I am getting the same errors.

There are problems with the repo, some servers are down. You can see [this bug report]("https://bugs.launchpad.net/medibuntu/+bug/252271").

I hope in the next few days everything will be OK.

---

### Post by Drizzel on 2008-08-08
Ahh I see.. Thank you! :)

---

