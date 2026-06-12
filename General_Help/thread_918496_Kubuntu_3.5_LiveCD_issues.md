---
title: "Kubuntu 3.5 LiveCD issues"
date: 2008-09-13
forum: General Help
---

### Post by elyktron on 2008-09-13
I looked around and couldn't find exactly what I was looking for but if this has already been addressed please point me in the right direction.

I'm working a project right now where we are doing a Kubuntu Hardy LiveCD deployment for CSR's to work from home instead of buying thin clients for each for cost effectiveness.

Ubuntu was chosen for its hardware detection and security implementation which we have found to be obviously different from a traditional desktop install.

At this point we have identified 2 initiatives that each have their own problems.

1.) We have to prevent the install from detecting and subsequently autoloading USB pen drives, host hard drives, firewire, extra CDRom drives, etc.  

After investigating choking the system by modify udev rules, modifying HAL rules, etc.  We have decided to simply change the permissions of /bin/mount to 0700 so that the root user can access it but the normal "ubuntu" live cd user cannot.  And making a rule change to HAL to prevent autoloading per a previous post elsewhere on the forums.

The problem however is that the root user and the ubuntu user have no passwords, are not locked and anyone with a brain can figure out in 2 seconds how to sudo or straight su to the root user to run the mount command.

We are building the live CD from a rootfs build directory that we squash and mkisofs but the problem we have found is that Ubuntu defines these users and creates the /etc/sudoers file on the fly somewhere during the build since the sudoers file and accounts we have predefined do not make it to the final ISO build.

So, I need to know how to "passwd -l root" AND use a sudoers config on the LiveCD that does NOT allow the regular "ubuntu" user sudo access or I need a better way to handle this.

2.) The second problem is more KDE centric in that we need to trim the K Panel menu so that it does not include things like Konsole, System Settings and the Run command but we have been unable to identify which config files are changed and what syntax changes are made to accomplish this.  We have tried making backups of the usual KDE directories, making a change and diff'ing the back up against the live config and running a "find / -mmtime -2" command to identify changed files system wide with no success.

I know this is long but I would sincerely appreciate any help you can offer, I have to figure out these last 2 initiatives by Monday or Tuesday as we need to move to the Beta testing phase of this project asap.

Short of booting to the LiveCD, making changes, replicating it to an HDD and then generating an ISO from the HDD image, I'm at a loss for how to handle these.

Also, please let me know if I've posted this to the wrong section... I wasn't sure where to put it.

Thanks!

---

### Post by tuxerman on 2008-09-13
> **elyktron said:**
> 
2.) The second problem is more KDE centric in that we need to trim the K Panel menu so that it does not include things like Konsole, System Settings and the Run command but we have been unable to identify which config files are changed and what syntax changes are made to accomplish this.  We have tried making backups of the usual KDE directories, making a change and diff'ing the back up against the live config and running a "find / -mmtime -2" command to identify changed files system wide with no success.
Thanks!

For this problem, you can use the handy KMenu editor: Right click the K button (and unlock the panels if they are locked) and select Menu Editor. Yu can choose what to display in teh menu from there.

---

### Post by elyktron on 2008-09-13
> **tuxerman said:**
> For this problem, you can use the handy KMenu editor: Right click the K button (and unlock the panels if they are locked) and select Menu Editor. Yu can choose what to display in teh menu from there.

We did that but that doesn't tell me where the changes are saved at the system level.  When booting from LiveCD we have to be able to make that change stick by building it into the ISO so I have to know where its making the change on the filesystem in order to include the relevant configuration file changes in the build.

So, I know I can do it through the GUI but when doing so, what files at the system level are changed to reflect this.

Make sense?

Thanks for your input!

---

### Post by elyktron on 2008-09-13
Need to clarify... I didn't mean to say that Kubuntu 3.5 is what I was using... I meant to say Kubuntu with KDE 3.5 is what we were using.

Not that important... just didn't want to make it sound like we were using some REALLY outdated version of Kubuntu.

Anyone have any ideas on these 2 problems?

---

### Post by tuxerman on 2008-09-14
> **elyktron said:**
> 
So, I know I can do it through the GUI but when doing so, what files at the system level are changed to reflect this.


As far as I know, the entire ~/.kde folder has your settings in KDE. Try searching inside that for specific files. Feel free to ask if you want to know more :)

---

### Post by elyktron on 2008-09-14
> **tuxerman said:**
> As far as I know, the entire ~/.kde folder has your settings in KDE. Try searching inside that for specific files. Feel free to ask if you want to know more :)

If you know the specific files I'd appreciate it if you could tell me.  We copied this directory, made a change and then looked for the changed files.  We only found 3 (don't remember what they were) but we didn't see anything in them that pertained to the menu.  It was more like when clicking Ok to save the changes it just overwrote all the corresponding config settings instead of making an incremental change.  One of the files I think was kdeglobals or something like that.

Also, for initiative #1 I found this link [here](https://help.ubuntu.com/community/LiveCDCustomization) which explained where to make the change.  It was under the Advanced customizations near the bottom 1/3rd of the page.

---

