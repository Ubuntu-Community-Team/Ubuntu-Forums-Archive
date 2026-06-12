---
title: "radeon assert failed"
date: 2010-12-10
forum: Hardware
---

### Post by thornate on 2010-12-10
I have a Toshiba A75-S125 notebook with Radeon graphics card (lspci lists it as "*ATI Technologies Inc RS300M AGO [Radeon Mobility 9100IGP]*") and Ubuntu 10.10 just installed. When I run glxgears, it opens fine and starts animating, but if I try to resize it I get the error message:
*../../radeon/radeon_cs_gem.c:181 cs_gem_write_reloc: Assertion 'boi->space_accounted' failed.*

This has also happened on other programs that use OpenGL. What can I do to fix this?

---

