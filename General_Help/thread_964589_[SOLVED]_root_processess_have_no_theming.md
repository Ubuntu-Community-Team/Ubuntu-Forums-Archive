---
title: "[SOLVED] root processess have no theming"
date: 2008-10-31
forum: General Help
---

### Post by paranoid_humanoid on 2008-10-31
Hi, this is a really weird problem. The apps that i run as root like synaptic all run with no themes. I think it's a problem with gnome-settings-daemon, it happened to me once before on hardy and it went away by itself.
I'm on intrepid now, a fresh install, and the problem came up again.
any ideas?

---

### Post by marshalium on 2008-10-31
The only time I have encountered this was when using a theme that was installed locally to my regular user (by putting it in ~/.theme or something). 

Then when an app was run as root using sudo, g-s-d told the app to use my custom installed theme. The app looked for the theme in root's theme path and could not find it so it displayed no theme.

I'm not sure if you are experiencing the samething. If "fresh install" means you didn't install any themes then its probably something different.

---

### Post by paranoid_humanoid on 2008-10-31
i think that's exactly what i'm doing. my themes are in ~/.themes, what's the shared theme directory?

---

### Post by paranoid_humanoid on 2008-10-31
okay i got it. i moved my themes to /usr/share/themes and everything worked perfectly.
thanks :)

---

