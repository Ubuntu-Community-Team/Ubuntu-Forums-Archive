---
title: "Getting Rockbox to work with Rhythmbox"
date: 2008-11-26
forum: Hardware
---

### Post by sampattuzzi on 2008-11-26
I just quickly wanted to share something I think others may find useful if they are having problems getting a rockbox iPod to work under Ubuntu with Rhythmbox.

Basically the problem is that, though your iPod has a different firmware on it, it is still detected by Gnome as a standard iPod. This causes all sorts of problems with applications treating your Rockbox iPod as the standard iPod that only accepts aac and a database.

The quick fix that I found was as follows:

Firstly we need to backup the file we are about to change, press alt+f2 and then paste the following into the box:
gksu cp /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi.backup

We now need to open up the file that tells Gnome (and more specifically a program called HAL) how to dectect the hardware and what it is capable of. Press alt+f2 and then paste the following into the box:
gksu gedit /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi

There will be, near the top, a piece of text that looks like this:
<match key="info.category" string="storage">
<!-- Apple iPod - TODO: use USB ids to determine exact output formats -->
<match key="storage.vendor" contains="Apple">
<match key="storage.model" contains="iPod">
<addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
<addset key="portable_audio_player.access_method.protocols" type="strlist">ipod</addset>
<append key="info.capabilities" type="strlist">portable_audio_player</append>
<addset key="portable_audio_player.output_formats" type="strlist">audio/aac</addset>
<merge key="storage.requires_eject" type="bool">true</merge>
</match>
</match>

You need to change it too look like this:
<match key="info.category" string="storage">
<!-- Apple iPod - TODO: use USB ids to determine exact output formats -->
<match key="storage.vendor" contains="Apple">
<match key="storage.model" contains="iPod">
<append key="info.capabilities" type="strlist">portable_audio_player</append>
<merge key="info.category" type="string">portable_audio_player</merge>
<merge key="portable_audio_player.type" type="string">generic</merge>
<merge key="portable_audio_player.access_method" type="string">storage</merge>
<merge key="portable_audio_player.storage_device" type="copy_property">info.udi</merge>
<append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
<append key="portable_audio_player.output_formats" type="strlist">application/ogg</append>
<append key="portable_audio_player.input_formats" type="strlist">audio/x-wav</append>
<merge key="storage.requires_eject" type="bool">true</merge>
</match>
</match>

Now just save the file and close. That's it, now you should be able to use Rhythmbox or Banshee to upload media to your iPod.

---

### Post by mperry on 2008-11-26
I have a rockbox'ed 5th gen ipod. I select not to have any graphical programs open when I connect it and I turned off the entry in gconf editor to automatically mount external drives. Then I create a /etc/fstab entry for it and mount it on the command line. Then I rsync music to it or use grsync.

I prefer to have the rockbox'ed ipod show up as a basic usb drive and treaet it as such since that's the main reason I use rockbox. Then its just a matter of a simple rsync script to manage the mp3s in the music directory on it.

---

### Post by sampattuzzi on 2008-11-27
That is the great thing about Rockbox, that you can just use it as a USB drive. But it really should be supported as a media player of it's own by HAL.

---

### Post by jamesisin on 2010-11-09
Agreed.  I'd love to see better support for RockBox.  My collection is way to large to use a simple rsync for loading my iPod (an order of magnitude too small—60 GB v 600 GB).  I need to be able to select by playlists or something similar.

---

