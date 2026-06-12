---
title: "[SOLVED] Foobilliards, Cannon Smash and opengl"
date: 2008-08-30
forum: General Help
---

### Post by Bucky Ball on 2008-08-30
Hi all.

Posted earlier and fixed a couple of things but this persists, despite my researching. Maybe missing something obvious.

Hardly ever play games on my laptop, but one game I can sometimes not resist is Foobilliards (and congrats to the developers - cool and realistic).

Thought I'd stop work and have a quick game last night, open the game from Applications->Games->Foobilliards and the screen just kinda flickers and that's it (no gui). Was working fine last time I played.

Hmm. So I installed a ping pong simulation, Cannon Smash, to check if that was giving the same result and sure enough, nothing. I could hear the ping pong ball getting smashed about, just no game gui. Or, I figure, invisible GUI. Weird me out!

So, Foobilliards is 'a 3D billiards game using OpenGL' and since Cannon Smash 'relies on OpenGL-compatible rendering,' thought this might be the problem. Tried installing 'python-opengl' via synaptics but no different. Am using gnome desktop (don't like kde).

Not a major 'end of the universe data destruction' problem, but damned annoying and mysterious none the less (esp when it was working fine 3 weeks ago). Can't remember tweaking anything that might have effected this. Any and all suggestions greatly appreciated ... :)

---

### Post by Bucky Ball on 2008-08-30
Here is a list of the last 50 things removed. Maybe one of these has caused this problem with the game graphics. Some of them certainly have something to do with graphics but wouldn't know where to start pinpointing which it might (or might not!) be ...

```
skulker@HPLappy:~$ cat /var/log/dpkg.log | grep ' \(remove\|purge\) '
2008-08-02 02:05:36 remove libakonadiprivate0 0.82.0-0ubuntu2~hardy1~ppa3 0.82.0-0ubuntu2~hardy1~ppa3
2008-08-10 18:28:05 remove rhythmbox 0.11.5-0ubuntu8 0.11.5-0ubuntu8
2008-08-15 01:48:27 remove viewpdf.app 1:0.2dfsg1-3 1:0.2dfsg1-3
2008-08-15 01:48:27 remove gnustep-back0.12 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-back0.12-art 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-gpbs 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-gui-runtime 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-15 01:48:28 remove libgnustep-gui0.12 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-15 01:48:28 remove gnustep-base-runtime 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-15 01:48:28 remove libgnustep-base1.14 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-15 01:48:28 remove libobjc2 4.2.3-2ubuntu7 4.2.3-2ubuntu7
2008-08-15 01:48:28 remove libpopplerkit0 0.0.20051227svn-5 0.0.20051227svn-5
2008-08-15 01:48:53 remove etw 3.2+svn125-1 3.2+svn125-1
2008-08-15 01:48:54 remove etw-data 3.2+svn125-1 3.2+svn125-1
2008-08-16 19:40:23 remove abuse 1:0.7.0-6 1:0.7.0-6
2008-08-16 19:40:23 remove abuse-frabs 2.10-7ubuntu2 2.10-7ubuntu2
2008-08-17 04:35:00 remove smbfs 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
2008-08-17 04:35:44 remove gsambad 0.1.9-2ubuntu1 0.1.9-2ubuntu1
2008-08-17 04:35:44 remove samba 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
2008-08-26 18:30:26 remove wine 1.1.0~winehq0~ubuntu~8.04-1 1.1.0~winehq0~ubuntu~8.04-1
2008-08-30 00:00:22 remove fltk1.1-games 1.1.7-6 1.1.7-6
2008-08-30 00:00:26 remove foobillard 3.0a-3ubuntu1 3.0a-3ubuntu1
2008-08-30 00:00:26 remove libfltk1.1 1.1.7-6 1.1.7-6
2008-08-30 00:06:41 remove csmash 0.6.6-6.3ubuntu1 0.6.6-6.3ubuntu1
2008-08-30 00:06:41 remove csmash-data 0.6.6-6.3ubuntu1 0.6.6-6.3ubuntu1
2008-08-30 00:06:41 remove foobillard 3.0a-3ubuntu1 3.0a-3ubuntu1
2008-08-30 21:33:19 remove gnustep-back-common 0.12.0-1 0.12.0-1
2008-08-30 21:33:21 remove gnustep-gui-common 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-30 21:33:21 remove gnustep-base-common 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-30 21:33:21 remove gnustep-common 2.0.2-1 2.0.2-1
2008-08-30 21:33:22 remove libffcall1 1.10+2.41-3 1.10+2.41-3
2008-08-30 21:33:22 remove winbind 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
```

Help required as getting not far on this ... :)

---

### Post by Bucky Ball on 2008-08-31
And here is how I solved it:

I went to System->Administration->Hardware Drivers and found that the Nvidia driver was installed and ticked but not in use. I unticked it then ticked it again, restarted machine and all is well that ends well.

---

