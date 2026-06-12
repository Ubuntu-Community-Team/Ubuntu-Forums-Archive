---
title: "about uif2iso&quot;the compressed LZMA input is wrong&quot;,why?"
date: 2008-08-29
forum: General Help
---

### Post by maymore on 2008-08-29
maymore@maymore-desktop:~/src$ uif2iso /home/maymore/123.uif /home/maymore/123.iso

UIF2ISO 0.1.6
by Luigi Auriemma
e-mail: [email]aluigi@autistici.org[/email]
web:    aluigi.org

- open /home/maymore/123.uif

  file size    000000008efe50f7
  version      4
  image type   8
  padding      0
  sectors      1302321
  sectors size 2048
  blhr offset  000000008efda0e5
  blhr size    45074
  hash         003d551aab2b5a19c0d4fa9616206464
  others       00000040 00000000 01 02 02 00 00000000

- enable magiciso_is_**** encryption
- ISO output image format
- create /home/maymore/123.iso
- start unpacking:
  000%
Error: the compressed LZMA input is wrong or incomplete (0)

---

### Post by artistgay on 2008-11-06
obviously magiciso is still not all that bad like the author of uif2iso claims, because it worked on my uif file while his program failed with the same error message

the compressed LZMA input is wrong or incomplete

---

