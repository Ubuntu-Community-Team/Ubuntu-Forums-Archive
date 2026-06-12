---
title: "LTSP fat client problem"
date: 2008-11-03
forum: General Help
---

### Post by tegel123456789 on 2008-11-03
Hi,

I have been trying to setup LTSP with the [fat-client plugin]("http://www.nubae.com/ltsp-linux-terminal-server-project-netbooted-fat-client-for-ubuntu-hardy-and-intrepid") on 8.04 server using "ltsp-build-client --chroot fati386 --fatclient Ubuntu".
, but the thin fat client is unable to start x. All I see is the edubuntu splash screen with a progress bar that never finish. Using -nosplash option, I see this:

"Can't set permissions on mtab: Operation not permitted "

In the [fat-client script file]("http://www.nubae.com/hardy/030-fatclient") for hardy, I had to comment out the following line
*sed -ie "s/<allow_active>auth_admin_keep_always<\/allow_active>/<allow_active>yes<\/allow_active>/" /usr/share/PolicyKit/policy/org.freedesktop.hal.storage.policy*
otherwise I couldn't build the client image because the file *org.freedesktop.hal.storage.policy* wasn't found. Could that be related the the problem I have?

NFS is installed on the server and the /home folder is shared ( I can mount it on other pc:s on the subnet)

Thanks in advance!

---

