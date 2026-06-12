---
title: "rtorrent: &quot;Invalid or incomplete multibyte or wide character&quot;"
date: 2008-09-05
forum: General Help
---

### Post by jellysandwitch on 2008-09-05
[http://ubuntuforums.org/showthread.php?t=563961&highlight=Invalid+or+incomplete+multibyte+or+wide+character]("http://ubuntuforums.org/showthread.php?t=563961&highlight=Invalid+or+incomplete+multibyte+or+wide+character")

^^ This thread ^^ appears to discuss the same problem - but as you can see it wasn't solved for torrent files, only existent files that can be tar'd up.

The exact error occurs when I hit CTRL+S (to start the download of the torrent) in the client `rtorrent`:

```
( 1:06:49) Could not open file "./Classical Music Top 100/002. Johann Sebastian Bach - Matthäus Passion (BWV 244) - Erbarme Dich.mp3": Invalid or incomplete multibyte or wide character
```

Any ideas on how to fix it? The character is the a with umlaut

---

### Post by jellysandwitch on 2008-09-08
The problem appears to be solved by removing "UTF8" from your locale. For example, if your locale settings were "en_GB.UTF8", set it to "en_GB" to resolve the "Invalid or incomplete multibyte or wide character" complaint.

---

### Post by cav on 2008-11-12
As jelly mentioned, this problem definitely has something to do with *.UTF8 locale settings.
(just in case anyone does not know: to check your settings open a shell and type "locale" or check your environment variables with "env")


In my case, however, there was another primary reason for this problem: **NTFS** mounted with the some *.UTF8 locale option.

So best **download to some other filesystem**.
(Or maybe at least make sure you didn't mount the NTFS partition that way, didn't check that yet. See "man mount" and "man ntfs-3g" for details on that.)

In my case, for some strange reason it didn't help using the normal bittornado gui client and download to some ext3 FS, 'cause then I got some phyton error.
If you're encountering the same problem, and just want a quick pragmatic solution for just one torrent, the solution (or workaround, if you prefer) I used might come in very handy:

Open a shell and use the **command-line torrent client "btdownloadheadless"** that comes with the bittornado package.
You may want to change the locale for that shell if you like, but I've tried it without that as well and strangely **it worked for me using the default locale "en_US.UTF8"**, as long as I would download to some other FS (in my case ext3).

```
export LANG=de_DE
btdownloadheadless <torrent file>
```

Hope that helps

------------------------------------------
Edit: I figured the **bittornado gui client phyton error** out as well:

The problem arises if your bittornado defaults to some NTFS directory for download, even if it prompts for the directory immediately at startup and you change it to some other partition/FS.
Solution: You have to change the default download directory and restart bittornado.

---

