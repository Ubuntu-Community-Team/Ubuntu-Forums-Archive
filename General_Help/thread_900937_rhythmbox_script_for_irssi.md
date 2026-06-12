---
title: "rhythmbox script for irssi"
date: 2008-08-25
forum: General Help
---

### Post by anlag on 2008-08-25
Quick question - does anyone know of an irssi script that can display what song is currently played in my rhythmbox music player? I've seen a few for xmms, mp3blaster et al, but nothing for the standard Gnome player.

Alternatively, if it's possible that with relatively simple efforts add rhythmbox suppor to an existing script. I do some scripting and programming, but haven't really done anything like this.

Cheers.

---

### Post by QwertyManiac on 2008-11-30
Here's a simple one I got:
```
#!/usr/bin/perl -w

BEGIN{
use vars '$hook','$info';
eval q {
use Irssi;
};
$hook = !!$@;
}

sub np
{
$info = `rhythmbox-client --print-playing-format %ta\\ -\\ %at\\ -\\ %tt\\ -\\ "(%td)"`;
chop $info;
Irssi::active_win->command("/me is now playing: ".$info);
return 1;
}

if ($hook){
rb();
}else{
Irssi::command_bind('np', 'np')
}
```

Save it as a perl script (rhythm.pl) under ~/.irssi/scripts/ or under ~/.irssi/scripts/autorun, as preferred.

Original source from [this blog]("http://sicutdeux.wordpress.com/").

---

### Post by starscalling on 2009-01-03
> **QwertyManiac said:**
> Here's a simple one I got:
```
#!/usr/bin/perl -w

BEGIN{
use vars '$hook','$info';
eval q {
use Irssi;
};
$hook = !!$@;
}

sub np
{
$info = `rhythmbox-client --print-playing-format %ta\\ -\\ %at\\ -\\ %tt\\ -\\ "(%td)"`;
chop $info;
Irssi::active_win->command("/me is now playing: ".$info);
return 1;
}

if ($hook){
rb();
}else{
Irssi::command_bind('np', 'np')
}
```

Save it as a perl script (rhythm.pl) under ~/.irssi/scripts/ or under ~/.irssi/scripts/autorun, as preferred.

Original source from [this blog]("http://sicutdeux.wordpress.com/").

rhythmbox-client --print-playing-format %ta\\ -\\ %at\\ -\\ %tt\\ -\\ %ag\\ -\\ "(%te/%td)"

14:08:05 * [rip]oink is now playing: Lemon D - The Crash Test EP - Bring the Funk Baby - Drum And Bass - (1:06/7:11)
14:08:33 &[rip]oink> artist/album/track/genre/elapsed-total


great scripty~!~

---

