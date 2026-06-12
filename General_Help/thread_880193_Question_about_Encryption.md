---
title: "Question about Encryption"
date: 2008-08-04
forum: General Help
---

### Post by solwic on 2008-08-04
I've been reading up on the process of encrypting my hard drive, and I have a few questions.  (For the record, I'm talking about the LVM/Encryption option in the Ubuntu Alternate Install Disc)

1)  Does this encryption protect every partition?  I'm talking about a whole drive for Ubuntu - no dual booting.  I would have a boot partition, a root partition, and a swap partition.  Would they all be encrypted?

2)  Is this encryption really that secure?  For instance, this process protects my drive if someone were to pull it out of my PC and put it into another PC, as a secondary drive, right?  Does it help at all with online security (if, on the off chance, I *were* to be hacked)?

3)  Are there performance issues associated with encryption?  I installed an encrypted Ubuntu in VirtualBox and it was pretty slow, but I'm not sure if that was because of the encryption or because Ubuntu on VirtualBox is just...well...slow.  

4)  In theory, how long would it take to break this encryption of someone were to steal my drive?

5)  What happens if I forget the encryption password?  Can I format over it?  Is there a way to retrieve it?

I have a dual-boot right now (cousin is in town, loves PC games...I installed Windows for him) but I'm not keeping it.  I thought I would ask these questions now, before I reinstalled Ubuntu, so I could do it right the next time.

Thanks!

---

### Post by solwic on 2008-08-04
EDIT:  I found a few articles to answer some of my questions, so I guess I don't need help anymore.  

If anybody else cares (and can't get answers to their questions about this stuff), here's what I found out:

1)  It does protect the whole drive, unless you dual boot in which case you need to create a separate /boot partition.

2)  It's not "uncrackable" but it'll (supposedly) keep the average laptop thief out of your private files.  As for helping protect with online security - no answers available (that I could find, anyway).

3)  The CPU has to do extra "crypto-work" when reading/writing to the hard disk, but the effects are "supposed" to be negligible as far as speed and unit stress are concerned.  

4)  See #2.  I couldn't get estimates.  

5)  You cannot recover the password.  The tutorials I found suggest writing down the (recommended 20 characters and up) password and storing it separately from the computer, which totally defeats the purpose of having a passkey-secured hard drive (in my opinion...what happens if you're at a business meeting and forget the password.  Unless it's written down and on you at the time, you're S.O.L.  But if you carry the password with you, in a way that you'll always have it with the computer, chances are it could be stolen *with* the computer, making the whole process pointless.  

The results are mixed for dual-booting, too.  Some sites say you can, just leave the /boot directory on its own partition and unencrypted, others say you must devote a whole drive to the process.  Personally, I don't think anybody really knows for sure.  :P

:cool:

---

### Post by pytheas22 on 2008-08-04
I haven't actually done this myself, but I looked into once at work; I'm also relatively familiar with TrueCrypt, which is what this process uses, I think.
> 
Does this encryption protect every partition? I'm talking about a whole drive for Ubuntu - no dual booting. I would have a boot partition, a root partition, and a swap partition. Would they all be encrypted?

I think so, but don't quote me on that.
> 
Is this encryption really that secure?

Yes, TrueCrypt is really secure provided you choose a long, non-dictionary-word password.  And yes, it totally prevents people from reading your drive even if they were to take it out of your computer. 
> 
Does it help at all with online security (if, on the off chance, I were to be hacked)?
> 
Are there performance issues associated with encryption? I installed an encrypted Ubuntu in VirtualBox and it was pretty slow, but I'm not sure if that was because of the encryption or because Ubuntu on VirtualBox is just...well...slow.

I don't think there are performance issues.  Boot may be a little slower, but beyond that the system should run normally.  I could be wrong--I emphasize again that I've never actually tried this (although I hope to get around to it soon)--but I think that the partitions get unencrypted at boot, and after that everything runs as it would on any other system.

Probably not--when your system is up, nothing is encrypted, so an exploit can run wild (if it can get past all the other security barriers, of course).  Online security is a whole different game.
> 
In theory, how long would it take to break this encryption of someone were to steal my drive?

If you choose a good password and a good encryption algorithm (all of them are pretty decent), it could take really long, like the age of the universe, to crack the password using a modern computer.
> 
What happens if I forget the encryption password?

You're probably out of luck, unless you have the age of the universe to spend recovering your password.  Don't forget your password.

There's some [crazy stuff]("http://citp.princeton.edu/memory/") that some people at Princeton did showing a way to recover encryption passwords, but it only works if you gain access to a machine within minutes of when it's turned off.  In reality, full-disk encryption using TrueCrypt should be very secure.

I wrote this quickly and could be wrong about some stuff--hopefully someone more knowledgeable will also contribute--but I hope it helps.

---

### Post by solwic on 2008-08-06
Anybody else care to chime in here?  I'm going to be formatting in the next day or so and would really like as much info as I can get about this.  

Any, any help, suggestions, ideas, whatever would be greatly appreciated.  

Cheers!

---

### Post by devman on 2008-08-06
TrueCrypt uses AES-256 by default, I'm not sure about the FDE so someone else will have to chime in. AES is the name of the standard the original cipher was known as Rijndael. Rijndael was selected from a field of competing ciphers during a selection process (which also included Twofish and Serpent, also ciphers in TrueCrypt). NIST made the actual selection but Rijndael was also endorsed by the NSA (AES is used to safeguard classified documents). The cipher has been well vetted and there are no known cryptographic weaknesses in it. Barring some breakthrough mathematics or significant advances in computing (and our understanding of solving difficult problems) it will likely remain like that for the foreseeable future.

With AES-256 you have a key size of 256 bits. That means there are 2^256 (approx. 10^77, to give you handle on that number it is estimated that there are about 10^80 particles in the observable universe) possible permutations for the key. Lets say you had a quad-core processor running at 2.4GHz with a program that could make one key attempt per clock-cycle and was perfectly parallel (and this is a gross over-estimation) That's  9.6 billion keys tested per second. It would take you approximately 10^67 seconds to try them all. That's about 10^59 years (many times the current estimated age of the universe.) And even if you throw thousands or even millions of times that computing power at the problem, you are only reducing it by scalar amounts.

It's more than likely that any flaws in the security system provided by TrueCrypt would not be caused by a weakness in the cipher itself but a flaw in TrueCrypt's implementation or the hardware it resides on that allows for the key to be weakened (some sort of side channel attack).

---

