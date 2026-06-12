---
title: "Please help with really weird FS or ftp problem on ubuntu hardy"
date: 2008-07-22
forum: General Help
---

### Post by grooverider on 2008-07-22
hi ppl :)
I have a fresh install of ubuntu hardy (let's call this machine 1), i have several machines mainly unix machines on the network, i have setup samba, it works without problem between all clients. I also have a ftp running on machine 1, in the ftp dir i have all sorts of directories, including shares from other machines, which i mounted there with samba, i can see all files access everything and the rights are set correctly too, i can also download anything from machine 1's ftp directory as long as it is physically in that machines, when i try to download something from a mounted directory i get 2 different errors from several clients i have tried:

some clients give me this error:
150 Opening BINARY mode data connection for Arms.avi (734472192 bytes).
426 Sendfile error: Value too large for defined data type.

other clients give me this error:
150 Opening BINARY mode data connection for Fov.avi (731535360 bytes)
426 Transfer aborted. Operation not permitted

however when i download files which are only a couple kb it works, but i think no more then 10kb
then i tried uploading files to the ftp's directory into the directories which were mounted, and from which i can only downloadver small files or get the mentioned errors, uploading works, regardless the size
I have tried proftpd and glftpd on machine1 same problem, i have also installed an ftp on another ubuntu machine and have mounted directories from other machines (to recreate same circumstance) and there is no problem, so what the hell is the issue here, any hints tips?
thx :)

---

