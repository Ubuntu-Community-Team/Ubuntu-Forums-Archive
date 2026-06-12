---
title: "something about the &quot;root&quot; user"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by maorongzheng@gmail.com on 2009-03-30
If Ubuntu starts in recovery mode and with root auto login, the "root" can do everything with the all privilege without the password prompt.

Is that a potential security issue? If someone doesn't set password for the root user, everyone who has the chance to reach the computer will have the chance to control it .

In my thought, when the first User is created in installation, the password set for the first User should also be the default password to the "root" user.

---

### Post by mcduck on 2009-03-30
No, it's not a security issue. Or at last a meaningful one, as at the point when somebody is able to get a physical access to your computer (which is required for using the recovery mode) pretty much all security is already lost.

Person with a physical access can always use any Live-CD or bootable USB stick or removable disk to start the machine and access everything in the machine without any restrictions. Or just open the machine and take the hard disks & attach them to some other computer to access the files.

Because of this nothing that requires physical access to your computer can really be considered as security issue (at least from software point-of-view). If you care about security you'll make sure nobody can get his hands on your computer.

If you want, you can always protect the recovery mode by setting Grub password for it.

(having the same password for both root and the first user wouldn't make your system any more secure, actually more the opposite. And Ubuntu has very good reasons for disabling the root account anyway.)

---

### Post by albandy on 2009-03-30
add a password to grub, by default it's disabled. This is not a security issue, simply they know that when you have physical acces to a machine there's no possible security.

Grub it's like was your BIOS, and when you enter in recovery mode it's like if you were using the resuce CD.

---

### Post by tarps87 on 2009-03-30
It is technically a security vulnerability, but this depends on what your computer is doing. It is only really a problem were other people can access the machine.
As mentioned you can password protect it or remove it completely (not advised)

To stop people booting from a live cd/ USB you can disable this in the bios and then password protect the bios.
To stop people swapping the hard drive most computers have some sort of prevision for a lock which will stop access inside the case (unless they cut there way in)

Or if it is in your house you can lock the door :)

---

### Post by mcduck on 2009-03-30
> **tarps87 said:**
> It is technically a security vulnerability, but this depends on what your computer is doing. It is only really a problem were other people can access the machine.
As mentioned you can password protect it or remove it completely (not advised)

To stop people booting from a live cd/ USB you can disable this in the bios and then password protect the bios.
To stop people swapping the hard drive most computers have some sort of prevision for a lock which will stop access inside the case (unless they cut there way in)

Or if it is in your house you can lock the door :)

Disabling things in BIOS (And BIOS passwords) is pretty much as useless as any security measures can possibly be. With physical access to the machine BIOS can be reset in 5 seconds using the jumper on your motherboard. Even if there's no such jumper removing the CMOS battery and unplugging the machine clears the password in 15-20 minutes. And the locks normally used in computer cases all use the same key, everybody who has ever owned a computer case with a lock has that key.. ;)

To protect a computer you have to start by protecting the physical device itself. Everything else comes after that. If you don't trust the machines users you simply cannot give them physical access to the machine itself.

---

### Post by tarps87 on 2009-03-30
> **mcduck said:**
> Disabling things in BIOS (And BIOS passwords) is pretty much as useless as any security measures can possibly be. With physical access to the machine BIOS can be reset in 5 seconds using the jumper on your motherboard. Even if there's no such jumper removing the CMOS battery and unplugging the machine clears the password in 15-20 minutes. And the locks normally used in computer cases all use the same key, everybody who has ever owned a computer case with a lock has that key.. ;)

To protect a computer you have to start by protecting the physical device itself. Everything else comes after that. If you don't trust the machines users you simply cannot give them physical access to the machine itself.

I was talking about the holes that a lot of case manufactures provide, that will fit a standard size padlock, or chain. All these locks have unique key. Also once you have locked the case other than using a force full means of entry you can not remove battery or move any jumpers and I don't know about you but I wouldn't want to unplug the machine and hang around until the battery goes flat :)

---

