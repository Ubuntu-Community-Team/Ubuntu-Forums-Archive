---
title: "Problems running Matlab R14 under Kubuntu Breezy"
date: 2005-11-04
forum: General Help
---

### Post by derbaschti on 2005-11-04
Hi I am trying to run Matlab under Kubuntu Breezy. I followed instructions given here: [http://www.ubuntuforums.org/showthread.php?t=40997&highlight=matlab](http://www.ubuntuforums.org/showthread.php?t=40997&highlight=matlab)

But when I try to run Matlab ```
sudo matlab
``` I get the following error message:

/Matlab/matlab7/bin/glnx86/MATLAB: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Can anybody help me? Thanks a lot,

Sebastian

---

### Post by rmjokers on 2005-11-04
Sounds like you need to install the old libc++ library:

sudo apt-get install libstdc++5

I had to install this to run the new firefox beta.

---

