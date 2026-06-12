---
title: "CUPS gives 'unsupported format' after upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Deatzo Seol on 2009-11-02
After upgrading to Karmic my cups installation broke.

Apparently, there's something wrong with the mime/document-types support:
```

Print-Job client-error-document-format-not-supported: Unsupported format 'application/postscript'!

```

Well, not only application/postscript gives the error, *all* formats do...

Yes, I have uncommented application/octetstream in types.conv, ghostscript-cups and foomatic are installed and I have all drivers.

Very strange...
Any help?

---

### Post by Deatzo Seol on 2009-11-09
Anyone?

---

