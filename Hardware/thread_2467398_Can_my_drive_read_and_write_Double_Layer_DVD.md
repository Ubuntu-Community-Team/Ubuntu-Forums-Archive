---
title: "Can my drive read and write Double Layer DVD?"
date: 2021-09-25
forum: Hardware
---

### Post by idyllicgorilla on 2021-09-25
[B]Is there any trustworthy online database of the specifications of all manufactured drives?
[/B]
I would like to know if the drive in my laptop reads and writes dual-layer DVDs. I do not have any, even a clean, DVD-DL at hand. According to the cd-drive terminal command it is **PLDS DVD-RW DS8A9SH EL3A**. I cannot tell for sure from the "manual" ([http://www.bitsbytesdeals.nl/downloads/DS-8A9SH.pdf](http://www.bitsbytesdeals.nl/downloads/DS-8A9SH.pdf)). Writing an e-mail to the manufacturer of the drive/laptop is useless as the drive is from 2013.

 There are three lines about double-layer discs (-R and + R) but I don't know if I can believe it because the log ends in absurdity --> the recorder can write DVD-R but cannot write DVD-RW and DVD + RW. As far as I know, only the type of the disc (CD, DVD, BD) and capacity (SL, DL) matters and it makes no difference for the drive if a DVD is plus/minus or if a DVD is rewritable or not (R/RW).

```
                      Drive: /dev/sr0
            Vendor                      : **PLDS**    
            Model                       :** DVD-RW DS8A9SH  **
            Revision                    : **EL3A**
            Profile List Feature
                **DVD+R Double Layer - DVD Recordable Double Layer**
                DVD+R - DVD Recordable
                DVD+RW - DVD Rewritable
                [B]DVD-R - Double-layer Jump Recording
                DVD-R - Double-Layer Sequential Recording[/B]
                Re-recordable DVD using Sequential Recording
                Re-recordable DVD using Restricted Overwrite
                Re-writable DVD
                Re-recordable DVD using Sequential recording
                Read only DVD
                CD-RW Re-writable Compact Disc capable
                Write once Compact Disc capable
                Read only Compact Disc capable         
                       Core Feature         
                       Morphing Feature
                Operational Change Request/Notification supported
                Synchronous GET EVENT/STATUS NOTIFICATION supported         
                       Removable Medium Feature
                Tray type loading mechanism
                can eject the medium or magazine via the normal START/STOP command
                can be locked into the Logical Unit         
                       Write Protect Feature         
                       Random Readable Feature         
                       Multi-Read Feature         
                       CD Read Feature
                C2 Error pointers are supported
                CD-Text is supported         
                       DVD Read Feature         
                       Random Writable Feature         
                       Incremental Streaming Writable Feature         
                       Formattable Feature         
                       Management Ability of the Logical Unit/media system to provide an apparently defect-free space. Feature         
                       Restricted Overwrite Feature         
                       CD-RW CAV Write Feature         
                       DVD+RW Feature         
                       DVD+R Feature         
                       Rigid Restricted Overwrite Feature         
                       CD Track at Once Feature         
                       CD Mastering (Session at Once) Feature         
                       DVD-R/RW Write Feature         
                       Unknown code 33 Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Profile List Feature         
                       Hardware                                  : CD-ROM or DVD
            Can eject                                 : Yes
            Can close tray                            : Yes
            Can disable manual eject                  : Yes
            Can select juke-box disc                  : No         
                       Can set drive speed                       : No
            Can read multiple sessions (e.g. PhotoCD) : Yes
            Can hard reset device                     : Yes         
                       Reading....
              Can read Mode 2 Form 1                  : Yes
              Can read Mode 2 Form 2                  : Yes
              Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
              Can read C2 Errors                      : Yes
              Can read IRSC                           : Yes
              Can read Media Channel Number (or UPC)  : Yes
              Can play audio                          : Yes
              Can read CD-DA                          : Yes
              Can read CD-R                           : Yes
              Can read CD-RW                          : Yes
              Can read DVD-ROM                        : Yes         
                       Writing....
              Can write CD-RW                         : Yes
              **Can write DVD-R                         : Yes**
              Can write DVD-RAM                       : Yes
              [B]Can write DVD-RW                        : No
              Can write DVD+RW                        : No[/B]         
     

```

---

