---
title: "[SOLVED] Package Manager problems"
date: 2008-10-13
forum: General Help
---

### Post by Dave Otter on 2008-10-13
When I enter Synaptic Package Manager I get the following message:-
                 
          Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
    What does this mean and can I correct it

     Step by step so I can understand

                  Thankyou

---

### Post by homemadejam on 2008-10-13
> **Dave Otter said:**
> When I enter Synaptic Package Manager I get the following message:-
                 
          Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
    What does this mean and can I correct it

     Step by step so I can understand

                  Thankyou

I got this error the other night.
Someone has made a spelling mistake somewhere along the line... if someone could report it to the right people, that would be great!

okay, so you need to edit the file: /etc/apt/sources.list

and do a search for the word 'harty' and replace it with the word 'hardy'

then run  sudo apt-get update

That will sort out your problem.

Jam

---

### Post by Dave Otter on 2008-10-13
Where do I find apt/sources.list

---

### Post by fooman on 2008-10-13
> **Dave Otter said:**
> Where do I find apt/sources.list

if you need to edit the file as described above,  try:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Dave Otter on 2008-10-13
Thanks to homemadejam and fooman for replies

---

