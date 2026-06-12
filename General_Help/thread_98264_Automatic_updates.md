---
title: "Automatic updates?"
date: 2005-12-02
forum: General Help
---

### Post by kalahari875 on 2005-12-02
I am trying to add a script to cron.weekly to update Kubuntu that involves issuing three commands. I put them in a single executable script file, /etc/cron.weekly/dist-upgrade, as follows:

apt-get clean
apt-get update
apt-get dist-upgrade -y --purge

When this runs, though, anacron gives the the following error:

/etc/cron.weekly/dist-upgrade:
run-parts: failed to exec /etc/cron.weekly/dist-upgrade: Exec format error
run-parts: /etc/cron.weekly/dist-upgrade exited with return code 1

Any idea what the problem is? I know this is probably something simple. Is there some other way I should be trying to keep Kubuntu up-to-date? Thanks!

---

### Post by moberry on 2005-12-02
First off k/ubuntu automatically lets the user know when updates are available. I do not know how (Some one tell me). It looks like from the error the syntax is wrong. Try executing your script from a shell. Let me know how it goes.

---

### Post by guice on 2005-12-02
First line of the script must start with the shell the script's to run in: #!/bin/bash
And it must be executable. You should be able to run it via the command line.

---

