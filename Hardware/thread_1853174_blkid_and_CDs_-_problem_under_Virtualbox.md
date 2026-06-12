---
title: "blkid and CDs - problem under Virtualbox?"
date: 2011-10-01
forum: Hardware
---

### Post by W. Irving on 2011-10-01
Running blkid on a CD under lucid running in Virtualbox (host OS Windows XP, using passthrough for the drive) results in strange things happening.

With a data CD:
```
$ blkid /dev/sr0
$ echo $?
2

```
blkid finishes immediately. As for exit code 2... "If the specified token was not found, or no (specified) devices could be identified, an exit code of 2 is returned."

If instead I do..

```
$ blkid -p /dev/sr0
/dev/sr0: VERSION="Joliet Extension" LABEL="Version 2.01" TYPE="iso9660" USAGE="filesystem"
$ echo $?
0

```

..which takes blkid 3 seconds, and then examine the syslog..

```
[ 9302.458755] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9302.458767] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[ 9302.458776] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 9302.458786] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 40 ea 00 00 02 00
[ 9302.458799] end_request: I/O error, dev sr0, sector 1377192
```

.. a few dozen sections of the above.

Doing the same to an audio CD produces similar results, however even using the -p argument vill have blkid return nothing on stdout and exit code 2. Along with 

```
[ 9926.000600] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9926.000611] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[ 9926.000620] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9926.000632] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[ 9926.000644] end_request: I/O error, dev sr0, sector 4096
[ 9926.077401] Buffer I/O error on device sr0, logical block 1024
[ 9926.162648] Buffer I/O error on device sr0, logical block 1025

```

blkid will behave like expected with a DVD in the ODD, and not soil the syslog with these peculiar messages. What's the deal here? Is it Virtualbox messing things up, or is blkid not capable of working on CDs?

Could someone please test the above commands with a data CD and audio CD running lucid natively?

---

