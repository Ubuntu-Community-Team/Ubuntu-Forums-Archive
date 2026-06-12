---
title: "Sansa Clip (how it worked for me)"
date: 2008-09-12
forum: Hardware
---

### Post by notbitmonk on 2008-09-12
I recently bought a Sansa Clip 4GB for my daughter.  I asked Sansa support for ogg capabilities and this is what they said:
[INDENT]> Thank you for contacting SanDisk Technical Support. It is our goal to make sure you have all the resources you need to get the most from your product.

Please be note that the minimum system requirement for the Sansa Clip is Windows XP and a Windows Media Player 10. These are required for transferring subscription music which requires the player to be in "MTP" mode and the "MTP" drivers from the computer.

The player would recognize and play .ogg files and also can have the "MSC" mode (non-subscription music) by updating its firmware.

You may see how to update firmware on a Linux platform through this link:

[http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720)

MSC functions as a mass storage device, and will show up on your computer as an external drive (eg "E:\"), just like a USB key or portable hard drive. You can simply drag and drop your music files directly to the drive or folder of the player without using any application such as Windows Media Player.

MTP enables Windows XP, Vista and any other supported OS to recognize the device as a standard media device. If you are transferring music that you have purchased or music that are licensed and/or protected, then you need to use the MTP mode with the use of an application like Windows Media Player 10.

Should you have any further inquiries or concerns, please do not hesitate to reply to this message or send another inquiry via an Email.

Best regards,
Christine B.
SanDisk Technical Support[/INDENT]

I'm using Ubuntu 8.04 and Rhythmbox recognized the Clip.  I was able to move music to the Clip using Rhythmbox.  Upon playing it, I noticed that the music was labeled as Unknown.  After connecting the Clip back to my computer I explored the device and observed that my ogg files were transferred/converted as mp3s (and badly at it).  I deleted the files and transferred the ogg files directly.  However, playback of the ogg files did not work with the installed firmware (which I do not remember the version number).

At this point I followed the advice from Sansa support and updated the firmware manually to version 01.01.29.  Afterwards, the ogg files in the Clip played OK and were recognized by the clip (the ogg files were labeled properly in the Clip screen).  Still, transfer of files to the device had to be done manually since when I used Rhythmbox (again) to transfer other files, the ogg files were converted (again) to mp3.

FYI, the firmware updater from their page does not work using Wine 1.1.4.  Although it installs, it fails to launch the updater.

The problem with the transfer is only a minor inconvenience for me but it may be a major problem for my daughter (9 years old) since she is still learning how to use a computer.  The player is a nice buy (approximately $50 USD when I bought it two weeks ago at Costco) and I would recommend it to other users provided that it is updated to at least the version presented above.

--2008-09-23 Update--
Conversion is (apparently) done by Rhythmbox and not by the Clip (there is no information about this behavior in Rhythmbox webpage).  I checked using Winamp and files were transfered without conversion.  However, during this check I noticed that files viewable from Windows Explorer are different from files viewable from Nautilus (I'm using Ubuntu 8.04).  The files I transferred using Nautilus are not viewable from Windows Explorer, Windows Media Player or Winamp.  The files I transferred using Winamp are not viewable using Nautilus or Rhythmbox.  I think this has to do with MTP support.  Rhythmbox has an MTP plugin but when I activated it, my Clip was not recognized.  When I get the response from Sansa, I'll update this page.

--2008-10-06 Update--
The Clip default setting for MTP or MSC is "auto detect" (there are three settings: auto detect, MTP and MSC).  This means that under Windows it will work as MTP and under Linux it works as MSC.  The MTP plugin in Rhythmbox does not works even after setting the Clip to MTP (and after restarting the Rhythmbox and the computer).  The Clip is not even accessible or viewable through Nautilus when set to MTP mode.  Strangely enough, F-Spot thought that I had connected a camera, checked the Clip and was able to see the music files that came with the Clip (which can only be accessed in MTP mode).  

Using Windows, I set the Clip as MSC and started Winamp.  Winamp was not able to see the ogg files that I had transferred manually using Nautilus.  Media Player had the same behavior.  Both were able to see the mp3 files that I had transferred manually using Nautilus.  I didn't try transferring files using Winamp at the time to see if they were viewable with Rhythmbox or with Nautilus.  I'll try later and post my results back.

--2008-11-23 Update--
The Clip won't play Vorbis audio with the .oga extension.  This is the extension appended by oggencoder in Intrepid following the request by Xiph.  You can change the .oga extension to .ogg by renaming the file and the Clip will play it.  It is a hassle but is the only workaround I'm aware of (found the issue 15 minutes ago [2008-11-23, 2206 GMT-4]).  The latest firmware updates adds support for FLAC.  Check their page ([http://forums.sandisk.com/sansa/board?board.id=clip](http://forums.sandisk.com/sansa/board?board.id=clip)) and select the update based on your firmware version.  Version 1 can not update to version 2.  I made a post on the Sansa forums requesting that Sansa update the firmware to let the Clip recognize .oga files ([http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=11744&jump=true#M11744](http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=11744&jump=true#M11744)).

--2008-12-14 Update--
Peter, from the Rhythmbox list explained the following regarding why Rhythmbox changes ogg files to mp3.
> Rhythmbox is being helpful and transcoding your ogg files into mp3, because it doesn't know your player can cope with ogg files.  You need to create a file called .is_audio_player in the root folder of the device to tell RB this.  See the FAQ for details, [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ)
I followed the FAQ and created the following .is_audio_player file at the Clip root:
```
audio_folders=MUSIC/,RECORD/,AUDIBLE/,AUDIOBOOKS/,PODCASTS/,
output_formats=application/ogg,audio/ogg,audio/mpeg,audio/flac,audio/wave,audio/x-wav,audio/x-ms-wma,audio/x-ms-wmv,audio/audible,audio/x-pn-audibleaudio
```
Flac files, when transferred, are renamed to append a "01." at the beginning of the filename.  One thing that happened when adding the flac files when I didn't include the media type was that Rhythmbox changed the files to oga instead of mp3.  After playing a while to see what was going on I found out the Rhythmbox will encode files which the player (the Clip) doesn't support based on the first mime type of the list. Rhythmbox "knows" what file types the player supports based on HAL device information.  The .is_audio_player is a HAL override so Rhythmbox and other software "know better".

For those that add the .is_audio_player, remember that it will be handled as a hidden file by Nautilus and you need to check the "Show Hidden Files Option (Ctrl+H)" under the View menu to access it afterwards.

--2009-01-03 Update--
For those of you that transfer .oga files to the Clip and need to do some renaming, Mats Taraldsvik fron the Rhythmbox list provided the following script:
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import os, re

def rename(path) :
    for root, dirs, files in os.walk(path) :
        for name in files :
            prefix = name[:-4]
            postfix = name[-4:]
            if postfix == '.oga' :
                os.rename(root + '/' + name, root + '/' + prefix + '.ogg')
        
rename('/media/SANSA CLIP/MUSIC')

```
Copy it into your text editor and save it as fixogga.py.  This is Mats explanation on how to use the script.
> Just open a terminal and run it with '*python fixogga.py*' if the script is in your current directory, or '*python /path/to/fixogga.py*' if it lies elsewhere.

quick explanation:

the rename function takes the path as argument (in this case, the music folder of my sansa clip. You might have to change this path, if it is named differently.) and does a recursive traversal. If the last four characters of the file is '.oga', the file is renamed to '.ogg'.
Thanks to Mats and Peter for their help resolving this.

---

### Post by forger on 2008-09-12
edit: - ignore this post -

---

