---
title: "New Hard Drive Problems"
date: 2019-08-13
forum: Hardware
---

### Post by ringel052 on 2019-08-13
To start out with I'm fairly familiar with Ubuntu from a GFI user standpoint and can do some very basic commands in Terminal so for all intent an purposes I'm a Terminal noob.  I also searched the forums for my problem and either didn't understand what I was looking at or my specific problem wasn't addressed I really don't know.

Okay, tried to install a secondary hard drive for media storage, formatted in ext4.  Then I spent hours trying to figure out how to mount it but nothing would work until I did something, I know not what, that mounted the volume..........
Now it will not let me change permissions so I can write to it.  When I open Nautilus it tells me I have permission, when I open Nautilus as a super user it tells me the permissions are unknown.
Hopefully someone can point me in the right direction and please remember, you're talking to a noob not a techie.  
Thanks

---

### Post by ringel052 on 2019-08-13
Interesting, now when I check in Nautilus as a super user it's not there.

Okay, clicked on "mount" and it showed up when I logged into Nautilus as a SU.

---

### Post by yancek on 2019-08-13
Did you create a partition on the drive before formatting it?

Partitions on external drives on most Linux systems are available to access/mount under the /media or /media/username directory, usually by UUID.  If the referenced drive is the 2nd drive, it will likely be sdb.  You can get the UUID of partitions on that drive with the command:  sudo blkid  Run that and post the output here.

You can get the permissions by running:  ls -l /media/username (substitute your actual users name here)

If the partition you created on the 2nd drive is the first partition on that drive, the standard method to mount it is to first create a mount point (directory), then use the mount command to mount it as in the examples below.

> sudo mkdir /media/sdb1

> sudo mount -t ext4 /dev/sdb1 /media/sdb1

I expect you will not need to do this unless you want to as the partition is probably available under the /media/username directory mount point.

---

### Post by ringel052 on 2019-08-13
> **yancek said:**
> Did you create a partition on the drive before formatting it?

Partitions on external drives on most Linux systems are available to access/mount under the /media or /media/username directory, usually by UUID.  If the referenced drive is the 2nd drive, it will likely be sdb.  You can get the UUID of partitions on that drive with the command:  sudo blkid  Run that and post the output here.

You can get the permissions by running:  ls -l /media/username (substitute your actual users name here)

If the partition you created on the 2nd drive is the first partition on that drive, the standard method to mount it is to first create a mount point (directory), then use the mount command to mount it as in the examples below.





I expect you will not need to do this unless you want to as the partition is probably available under the /media/username directory mount point.
It's a secondary internal drive.  From what I read it didn't need to be partitioned just formatted so no, I don't think I did, did the formatting in Gparted.

[https://lh3.googleusercontent.com/AuwKHX0ioT3al-dsT7ZwSWGiIeEIv-DepPkQfdZn7lFyP92_GKVlQPtNnQF3UbduADAGPI2W8JXdkneoJL38D9My18bciQU7EYYZu19ehqHQl_DbwIHjv-O2ObpOfZazLZcUUDY8tsYHgpOf7EIxsLOS48P7lwWrbzqfE_XhLz1ahqunqNhjSfbe6Jqv9UpEDxStWBCtrpFSa7iH_1Vsza7YwSR2Rb_Gg4iS0YAiAR6M9LoZo91ZZA19VyMZs-FMmAg59_8qZWb35YIc4vqQsGKSqhVrfpCIQ7eIf93bJs697gg3RAk5o9TM-FhaM33HP85f930U1B29G2Xt5pHmr6MgEeHBF2M9jHpUz3s3E6AuZQ3Ig4cHxShwKgbDMvvUbHrWEmATdGh5yJdK74FeEMT0_iTH-6vHg9-1JIjx52dVYXPgZPS77e79naa3HuGWUMSshU7P_5fHcJCVk-Ea6WegzX2hvFxmB2e9SPDynl7LIPYq4MenIP7D0UucWUT37k3UtRCbPMJDbjHvhznLY0ynpciSTL8zJCuqxf7NZcBAYHK7Uq84qIOV8IYWqpw7WDkHaW6Fd3XPfoXOVyo3ZQDITcWl4NxhaXigEihiELTQCxCe6A2S3zi_9kIsPrEBkQTdCAcN_gwXFBginc6uKIXaiqOX3Pk=w727-h501-no](https://lh3.googleusercontent.com/AuwKHX0ioT3al-dsT7ZwSWGiIeEIv-DepPkQfdZn7lFyP92_GKVlQPtNnQF3UbduADAGPI2W8JXdkneoJL38D9My18bciQU7EYYZu19ehqHQl_DbwIHjv-O2ObpOfZazLZcUUDY8tsYHgpOf7EIxsLOS48P7lwWrbzqfE_XhLz1ahqunqNhjSfbe6Jqv9UpEDxStWBCtrpFSa7iH_1Vsza7YwSR2Rb_Gg4iS0YAiAR6M9LoZo91ZZA19VyMZs-FMmAg59_8qZWb35YIc4vqQsGKSqhVrfpCIQ7eIf93bJs697gg3RAk5o9TM-FhaM33HP85f930U1B29G2Xt5pHmr6MgEeHBF2M9jHpUz3s3E6AuZQ3Ig4cHxShwKgbDMvvUbHrWEmATdGh5yJdK74FeEMT0_iTH-6vHg9-1JIjx52dVYXPgZPS77e79naa3HuGWUMSshU7P_5fHcJCVk-Ea6WegzX2hvFxmB2e9SPDynl7LIPYq4MenIP7D0UucWUT37k3UtRCbPMJDbjHvhznLY0ynpciSTL8zJCuqxf7NZcBAYHK7Uq84qIOV8IYWqpw7WDkHaW6Fd3XPfoXOVyo3ZQDITcWl4NxhaXigEihiELTQCxCe6A2S3zi_9kIsPrEBkQTdCAcN_gwXFBginc6uKIXaiqOX3Pk=w727-h501-no)

---

### Post by ringel052 on 2019-08-13
Ran ls -l

[https://lh3.googleusercontent.com/gqxJiuEj0gD_Ig-0gRU1-eWtWzWMN5vcbpAOqtOxazu4QLg2oqbTRrGcdpEcBlASH0uHFGkFSkb7ijUyw-gtE2yucI9FMKreWHFeQ0EgIzTLtg5LYN_83V4pMMQ9SQYeSySVvLutTfWax82dTAq-lojG475dZMku7HdYurC6h4aZzqAzPra7Hu5gTdammV5HONUpPGck7uftGb_AhQeA82nRYhKnbp6zSN0AFzUsvXxJPop5MLufrUJUDQkxtMsdEGhfBwGvb-Kpqx-2kStzubZKIeFxB42zZrOg3UD_Hmh0_1lxnl4tEX2r5spIjihkcZ-9HqCHCSyedTfCkpC8giYpSEXyDAi_oKE7kvahh_DJ3NdIYIqBb9DnicRAw-Yn0jcFP_A64B_XjdlTQ3NbDJa25BY3gOy4GSKuihymp75TXf14Qw7hmQ2xiw8hIgawFJvIBn-031Kbk-pTNz5iI8Gn00P11IFOnLn0f4DRDDI2LxHh-SUoBco8uIbw1OiSmGUpojeKqKaPnjVx46Mk5oU0tz57Pp7eb7CxkCCm-n5lNjcaDSi-V_jJGvlb6SVUA71ny8QfMv1fXxp5lt6rU1DoZ2yDQeg-hQ94FgjdQGxf08tUSlm_96GBLsNenmU53VtNSfBas-CSJynQ5-lNkBZSZOuVJSE=w758-h459-no](https://lh3.googleusercontent.com/gqxJiuEj0gD_Ig-0gRU1-eWtWzWMN5vcbpAOqtOxazu4QLg2oqbTRrGcdpEcBlASH0uHFGkFSkb7ijUyw-gtE2yucI9FMKreWHFeQ0EgIzTLtg5LYN_83V4pMMQ9SQYeSySVvLutTfWax82dTAq-lojG475dZMku7HdYurC6h4aZzqAzPra7Hu5gTdammV5HONUpPGck7uftGb_AhQeA82nRYhKnbp6zSN0AFzUsvXxJPop5MLufrUJUDQkxtMsdEGhfBwGvb-Kpqx-2kStzubZKIeFxB42zZrOg3UD_Hmh0_1lxnl4tEX2r5spIjihkcZ-9HqCHCSyedTfCkpC8giYpSEXyDAi_oKE7kvahh_DJ3NdIYIqBb9DnicRAw-Yn0jcFP_A64B_XjdlTQ3NbDJa25BY3gOy4GSKuihymp75TXf14Qw7hmQ2xiw8hIgawFJvIBn-031Kbk-pTNz5iI8Gn00P11IFOnLn0f4DRDDI2LxHh-SUoBco8uIbw1OiSmGUpojeKqKaPnjVx46Mk5oU0tz57Pp7eb7CxkCCm-n5lNjcaDSi-V_jJGvlb6SVUA71ny8QfMv1fXxp5lt6rU1DoZ2yDQeg-hQ94FgjdQGxf08tUSlm_96GBLsNenmU53VtNSfBas-CSJynQ5-lNkBZSZOuVJSE=w758-h459-no)

---

### Post by ringel052 on 2019-08-13
Here's the error I get when trying to move anything over to the new drive.

BTW these are my DVDs I'm converting to MP4, I used Handbrake.

[https://lh3.googleusercontent.com/fOb3FhuCjwqIZEzeLipbYa352syMilyDj8kgDu9clpKI5uA5MrqoTm1ma-44W3dj5shFtv1Bj8_cWNm9l7X1oZJ8eGxm6hBkl2D7bF2iDku-3gQbog6osn26g-kqiqzpSjKqBauJLNJVWcXi0ptzFvK9PGKIvtc00EWujrWNKpTb_EPHOcKTESVp4Bd3gFWLKnbjZL7f10s9gnf51D5tLhwdpPRDtdGrHyrkOsoBtQOVZhh58Zgpor4CHjFbgyEjhTs8UFTPFGuX7YURaxAIzzZsBbGd2mBCXow_qunhH2Fct4nDKbgnubfJ8WHVCKbcJ9ddgDC-o6XJmBDwNT3zcKMfYhkbbQPR4VfOZyWN0Bpg7cmCBdiISOX_rW9ZfNTvAvUpfoB6lSEyP3i2SxzAejPJb0RYLzUmPt8CAecn1Rfp__sO_zWuFd-sJx_W395oQJeS4EwcvASlyv1CHLb9spiQzQBxAP94KCt5x9QetK6xzHYsuaXnKQxfRQaTOGil8-puq6CNBSEaPfEJj44R0-c2RjYBgCC8vJMcXoMmYP51GFRkd8wiucrGLTtiUD7-gxQxE-_7sVk9chCQhGD9Nuw9vbIzF089c7HzHaxRyOhD6-o6ibD1zCn6Ye0ukcxVa8qIoLDeiAnjuLey2w4lI1ibNPNlXuU=w890-h605-no](https://lh3.googleusercontent.com/fOb3FhuCjwqIZEzeLipbYa352syMilyDj8kgDu9clpKI5uA5MrqoTm1ma-44W3dj5shFtv1Bj8_cWNm9l7X1oZJ8eGxm6hBkl2D7bF2iDku-3gQbog6osn26g-kqiqzpSjKqBauJLNJVWcXi0ptzFvK9PGKIvtc00EWujrWNKpTb_EPHOcKTESVp4Bd3gFWLKnbjZL7f10s9gnf51D5tLhwdpPRDtdGrHyrkOsoBtQOVZhh58Zgpor4CHjFbgyEjhTs8UFTPFGuX7YURaxAIzzZsBbGd2mBCXow_qunhH2Fct4nDKbgnubfJ8WHVCKbcJ9ddgDC-o6XJmBDwNT3zcKMfYhkbbQPR4VfOZyWN0Bpg7cmCBdiISOX_rW9ZfNTvAvUpfoB6lSEyP3i2SxzAejPJb0RYLzUmPt8CAecn1Rfp__sO_zWuFd-sJx_W395oQJeS4EwcvASlyv1CHLb9spiQzQBxAP94KCt5x9QetK6xzHYsuaXnKQxfRQaTOGil8-puq6CNBSEaPfEJj44R0-c2RjYBgCC8vJMcXoMmYP51GFRkd8wiucrGLTtiUD7-gxQxE-_7sVk9chCQhGD9Nuw9vbIzF089c7HzHaxRyOhD6-o6ibD1zCn6Ye0ukcxVa8qIoLDeiAnjuLey2w4lI1ibNPNlXuU=w890-h605-no)

---

### Post by DuckHook on 2019-08-13
Please do not post large images to the forums because some people have limited bandwidth or are viewing on small screens.

It is not necessary to post screenshots of terminal output in any case. Terminal output can be copied and pasted into the forum posting box. Please post such output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

If an image must be included, please do so as an attachment using the paperclip icon in the advanced posting menu.

---

### Post by ringel052 on 2019-08-13
> **DuckHook said:**
> Please do not post large images to the forums because some people have limited bandwidth or are viewing on small screens.

It is not necessary to post screenshots of terminal output in any case. Terminal output can be copied and pasted into the forum posting box. Please post such output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the *Adv Reply* toolbar.

If an image must be included, please do so as an attachment using the paperclip icon in the advanced posting menu.
Sorry, will do that from now on once I figure out how to do that ( [noparse]```
 and 
``` ).

---

