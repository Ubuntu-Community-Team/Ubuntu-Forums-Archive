---
title: "CANNOT download  package &quot;fglrx&quot; from Ubuntu Archive"
date: 2013-01-10
forum: Hardware
---

### Post by wilsonmak on 2013-01-10
I'm using Mythbuntu 10.10

sudo apt-get install fglrx fglrx-dev fglrx-amdcccle

Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted fglrx i386 2:8.780-0ubuntu2
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted fglrx-amdcccle i386 2:8.780-0ubuntu2
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted fglrx-dev i386 2:8.780-0ubuntu2
  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx_8.780-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx_8.780-0ubuntu2_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.780-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.780-0ubuntu2_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-dev_8.780-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-dev_8.780-0ubuntu2_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I did try both apt-get update or --fix-missing; still no good!

Is there a way to download these package somewhere else?

Thanks,
Wilson

---

### Post by Cheesemill on 2013-01-10
Your having problems because 10.10 reached end of life nearly a year ago.

Because of this it no longer receives any bug fixes or security updates, and the repositories have been taken off-line.

I would seriously suggest upgrading to a version of Ubuntu that is still supported.

---

### Post by wilsonmak on 2013-01-10
This is a development box.  I just want to keep the things as it should as it's been running for almost two years.  Don't know if the box can still run after the upgrade.  
So you mean there is no way to get the packages from other places?

---

