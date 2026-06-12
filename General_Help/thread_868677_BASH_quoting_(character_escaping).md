---
title: "BASH quoting (character escaping)"
date: 2008-07-24
forum: General Help
---

### Post by botfish on 2008-07-24
I am using the following command from the command line to find empty directories excluding hidden directories (starting with ".")

How do I correctly escape it for use in a Bash script?

find . \( ! -regex '.*/\..*' \) -type d -empty

I've read the Bash manual and at the moment it seems impossible to me.

Thanks for any help.

---

### Post by justleen on 2008-07-24
find /home/leen/  ! -regex '\..*' -type d -empty

mind the full path here, using . will return a start string  "./."  so then you need

find . ! -regex '.\/\..*' -type d -empty

---

