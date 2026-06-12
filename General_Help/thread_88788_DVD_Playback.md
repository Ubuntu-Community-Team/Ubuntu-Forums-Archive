---
title: "DVD Playback"
date: 2005-11-11
forum: General Help
---

### Post by Aussie on 2005-11-11
Hello All,

I've been using Ubuntu now for about 2 weeks (so I'm a complete noob) and i absolutly love it.  It does everything i need (almost, hence the post) including my ipod all without viruses and spyware.  Very nice indeed.

Anyway, my problem is that I've installed the libdvdcss2 as per the Ubuntu starter guide and dvd's still don't work.  I've searched around here for the past couple of days and still cant find anything.  Xine is telling me that it can't find the plugin but i installed it.  I also installed mplayer, totem and ogle just in case but nothing with them either.  I installed all the win32 codecs and they work fine, its just the dvd I cant get working.  I also enabled DMA if that helps at all.

If anyone can help me out here that would be great.  

Thanks.

---

### Post by PaganHippie on 2005-11-11
DVD playback works fine for me, providing I've done things in the following order:

[1]  Install xine with all its dependencies
[2]  Install totem with the xine libraries
[3]  Enable DMA on the DVD drive

The win32 codecs, afaict, are gstreamer-specific and won't work under xine, so that shouldn't be an issue.  gstreamer gives me choppy and unreliable playback, which is why I'm using xine instead.

Then again, I'm in the U.S. and (if your screen name is any indication) you're in Oz, so there may be some 'DVD region' issues involved here.

... very far from an expert ... just my $0.02 worth ...

---

### Post by bluetoad on 2005-11-11
I'm in Australia  and have these 2 scenarios:

Box 1 - Hoary:
Don't seem to be able to get anything other than US
DVDs working.  That is with a BENQ DW-1620.  I had to do some argy bargy 
to get the DW1620 going.

Box 2 - Breezy upgraded from Hoary:
With a BENQ DW-1640 I got the Australian and US regions working. I can't remember if I tried the Aussie region DVDs before the upgrade.

I think both were on the same versions of libdvdcss2.  I have tried various versions on box 1.  I didn't use regionset on either drive - all regions should work.  Both drives are on the latest firmware and have DMA enabled.

Totem, xine and vlc give the same results.  Turning on the debug for libdvdcss 
(DVDCSS_VERBOSE=2) seemed to suggest a region issue.

So I might be able to help you somewhat.  But I'm no expert either...

...Peter

---

### Post by Aussie on 2005-11-11
Thanks guys,

I managed to get it to work.  My computer has both a DVD reader and a DVD writer.  I uninstalled xine and installed it again, then tried to watch a DVD in the reader...nothing.  Then I tried it in the writer, and it worked.  I can't be bothered trying to get it to work in both drives, so I'll leave it at that.

Thanks for your help guys.

---

### Post by bluetoad on 2005-11-11
Have you tried different regions?

---

### Post by rcerreto on 2005-11-11
libdvdcss is pretty clever in bypassing region protection.
I tested with European and American DVDs and they run great.

---

