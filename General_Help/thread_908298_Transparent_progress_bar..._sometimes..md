---
title: "Transparent progress bar... sometimes."
date: 2008-09-02
forum: General Help
---

### Post by 01000111 on 2008-09-02
Greetings all,
Whenever I copy files from one machine on my home network to another on my home network, the progress dialog box appears and identifies the file(s) being copied and percentage complete, but the progress bar is transparent.  When enough progress has been made that the bar would cross over the %complete text, the text turns white.

When copying files locally, everything works correctly.

I'm running Xubuntu 8.04 with compiz and emerald.  I have tried changing themes and theme engines, but no effect.

Any thoughts?

Thanks,
01000111

---

### Post by rondackcpu on 2008-09-02
I believe this to be a bug in the theme.  It may have its roots in the imported Debian code. In some themes it happens more than in others.  On the GNOME desktop, the theme "Glider" appears to be more affected than, say, "Clearlooks".  I have found a way to get the progress bar restored, at least temporarily, but I have not found a way to fix it permanently.

If you open <Preferences><Appearance><Theme><Color> and change the value of the toolbar color and back out through the close buttons, the progress bar is restored until something makes it fail again.  It may be minutes, days, or weeks until the failure.

I have not found what trips the progress bar to fail to appear.  I surely wish someone has that answer and will respond to our post.

CRS

---

