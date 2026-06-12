---
title: "updating/upgrading"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2006-02-04
Hi,

New to ubuntu (5.1)...from fedora world.

I am used to using smart to upgrade fedora. Can I use that on ubuntu too? Anyone else using it?

Are there any ubuntu users in China that can advise me on a 'repository' that has good bandwidth? My sources.list file seems to be set to 'http://cn.archinve.ubuntu.com' at the moment (is that chosen from the location I chose during the install?), but it is taking forever to update/upgrade. Is there a better one?

Max.

---

### Post by madmetal on 2006-02-04
you can easily upgrade ubuntu using upgrade manager.
it is at the system toolbar.

---

### Post by davidmaxwaterman on 2006-02-04
[QUOTE=madmetal]you can easily upgrade ubuntu using upgrade manager.
it is at the system toolbar.[/QUOTE]

Yes, I know that. Unfortunately, it uses apt-get, which doesn't support mixed architectures (ie having amd64 and x86 packages installed at the same time). This was the reason it was impossible to use apt-get on fedora anyway. Maybe this doesn't apply to ubuntu for some reason...

Also, smart automatically selects mirrors based on performance, so it was always pretty quick to upgrade, which is the problem I'm seeing now - even though I have the chinese mirror selected, it is incredibly slow to update/upgrade.

How can I speed it up?

Max.

---

