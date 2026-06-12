---
title: "Eject iPod on Amarok &quot;Disconnect&quot; Command"
date: 2008-08-30
forum: General Help
---

### Post by Ralph L on 2008-08-30
In order to eject the iPod on the Amarok "Disconnect" Command I have set the post-disconnect command to echo "admin_passwd" | sudo -S eject -m %d.  This works fine but requires changing the post disconnect command with each new password.  This is awkward.  Is there a better way?  One web site suggested setting the post disconnect to &#8220;kio_umountwrapper %d&#8221;, but I couldn't make this work.

Running Kubuntu hardy.

Thanks

Ralph

---

### Post by anjilslaire on 2008-08-30
On my daughter's IPod, I just click the "Disconnect" button in the AmaroK gui. I've never had to configure the commands, and its always ejected flawlessly.

Different IPod's may bw different, I suppose.

---

### Post by leenux on 2008-09-30
I know this is a few weeks past, but after a week of reading and trying different methods here's what finally worked for me.

kdeeject -q %m

The default was %d for the device, but I had to change to %m for the mount point and this finally worked for me.

Running Hardy 8.04 and this was with my 3rd gen Nano video.

Hope this helps someone!

---

