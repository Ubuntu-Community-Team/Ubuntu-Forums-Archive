---
title: "update Manager: Error Opening Cache"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Maleeq on 2009-05-06
Hi

I am running 9.04 Jaunty and installed some updates and applications on my system. I tried installing Amarok from the terminal and was told I have "unmet dependencies"....I did not attempt the installation again. Everything looked fine until I restarted my machine, and now I get this message whenever I start the update manager:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

Not, installation from the terminal, synaptic, update manager and even local *.deb files all fail with either of these error messages:

"E: Encountered a section with no Package: header
E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

OR

"Software index is broken.
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I then go into to inspect the file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages and noticed its has been replaced with an HTML file! This HTML file contains the homepage of the HotSpot provider I last used!!!

I have attached the file to this post.

Please, can anyone help me out?

Regards

---

### Post by Partyboi2 on 2009-05-06
HI, Open a terminal and try removing the file
```
sudo rm /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Package 
```
Then recreate the file with
```
sudo apt-get update
```

---

### Post by Maleeq on 2009-05-06
Thanks for the prompt reply.

I am at work now and behind a proxy/firewall: > sudo apt-get update never works for me here. I'll do it once I get home and let u know the outcome.

Thanks

---

### Post by Maleeq on 2009-05-06
Thanks a lot Partyboi2.

It fixed my problem.

Cheers!

---

