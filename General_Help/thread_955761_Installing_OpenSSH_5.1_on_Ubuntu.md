---
title: "Installing OpenSSH 5.1 on Ubuntu"
date: 2008-10-22
forum: General Help
---

### Post by Aysah on 2008-10-22
Currently we are running a redhat box and because of new demands by our customers we now have to offer SFTP on top of our hardware vpn connection.  

After much frustration and flaky support I bought a new server and threw Ubuntu on it.  I need OpenSSH 5.1 so each one of our clients has there own specific home directory.

I can't seem to find a deb for OpenSSH 5.1 anywhere.  I assume we have to compile at this point but I want to be sure that I'm sure  what I'm doing is correct.

Would it be safe to follow the following guide on an ubuntu box?

[http://adamsworld.name/chrootjail5.php]("http://adamsworld.name/chrootjail5.php")

---

### Post by Woody1987 on 2008-10-22
open up synaptic and type in openssh or open a terminal and type sudo apt-get install openssh-server

---

### Post by Aysah on 2008-10-22
> **Woody1987 said:**
> open up synaptic and type in openssh or open a terminal and type sudo apt-get install openssh-server

but wont that install versino 4.7?  or will it install 5.1 (the one I'm told I need)

---

### Post by porteclefs on 2008-10-23
1)sudo apt-get update
this makes sure you apt-get the most up-to-date version of whatever your getting.

2)sudo apt-get install openssh-server
done

---

### Post by david_lynch on 2008-10-23
> **Aysah said:**
> but wont that install versino 4.7?  or will it install 5.1 (the one I'm told I need)
FWIW ubuntu 8.10 will include openssh 5.10. In the meantime you should be able to find a port for hardy somewhere. It's better to use a package than a tarball to keep things sane and manageable.

---

