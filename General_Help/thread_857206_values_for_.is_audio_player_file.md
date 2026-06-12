---
title: "values for .is_audio_player file"
date: 2008-07-12
forum: General Help
---

### Post by kcy29581 on 2008-07-12
Hi all,

I am trying to get my Samsung P2 to work with Banshee/Rhythmbox. I realise I need to create a ".is_audio_player" file at the root folder of the device. My problem that finding all the accepted values for this file is almost impossible.

Here's what I have discovered: I am only allowed to use three keys:

[LIST]
[*]audio_folders
[*]folder_depth
[*]output_formats
[/LIST]
So far audio_folders and folder_depth are pretty straightforward. The key output_formats has many acceptable values but I cannot find anywhere that lists **all** of them.

Looking [here]("http://people.freedesktop.org/%7Edavid/hal-spec/hal-spec.html#device-properties-portable_audio_player"), it only lists a few acceptable values, even though this is the specification (look at the key portable_audio_player.output_formats). [This]("http://live.gnome.org/Rhythmbox/FAQ") Rhythmbox page only shows a generic configuration. Also, the file 10-usb-music-players.fdi (located at /usr/share/hal/fdi/information/10freedesktop) shows what players HAL is configured for; I could try and write down every single value, but then how would I know that I have **all** of them?

Does anyone know where to find all the values for these keys?

Thanks

---

### Post by zeroti on 2010-04-28
check these sites out:

[http://www.floccinaucinihilipilification.net/wiki/index.php/.is_audio_player_file_format](http://www.floccinaucinihilipilification.net/wiki/index.php/.is_audio_player_file_format)
[http://plugindoc.mozdev.org/winmime.php](http://plugindoc.mozdev.org/winmime.php)

or just search "mime types m3u" for the mime-type of m3u, etc.

---

