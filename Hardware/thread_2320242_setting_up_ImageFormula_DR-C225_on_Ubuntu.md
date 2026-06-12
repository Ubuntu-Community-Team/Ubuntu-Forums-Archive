---
title: "setting up ImageFormula DR-C225 on Ubuntu"
date: 2016-04-11
forum: Hardware
---

### Post by david388 on 2016-04-11
I just bought a Canon ImageFormula DR-C225 scanner.  My computer is  running the Ubuntu 14.04 operating system.  The scanner itself did not  come with a driver for Linux.  However, I was able to find one on [www.canon-europe.com]("http://www.canon-europe.com").   That driver, however, needs to be built using the autoconf, configure,  and make commands.  I am running into errors while attempting to build  it.

 
"Make" gets stuck trying to use a file that it can't  find.  I looked through all of the online forums I could find; many  mentioned similar issues, but none had a solution that worked for me.  I  called Canon's technical support line, and they told me that they don't  provide technical support for the Linux scanner driver.  They suggested  I call a local computer repair shop.  I left a message at a local  computer repair shop, and they didn't return the message.  I searched  for "Linux help [my city]," and was able to connect with a guy who  teaches Linux classes for a living, and he had to admit that he wouldn't  be able to help me with this.  I'm almost ready to send the scanner  back to the store.  It's a shame because this scanner got such great  reviews, for example, on pcmag.com ([http://www.pcmag.com/article2/0,2817,2472494,00.asp](http://www.pcmag.com/article2/0,2817,2472494,00.asp)).
 
If anybody here can make sense of it, the error message I get from "make" looks like this:
```

client.c:30:24: fatal error: sane/sanei.h: No such file or directory 

 #include "sane/sanei.h"
                        ^
compilation terminated.
```

I have inspected the client.c file, and it contains the following:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/socket.h>
#include <limits.h>
#include <errno.h>
#include <sys/wait.h>
#include "sane/sane.h"
#include "sane/sanei.h"
#include "sane/sanei_net.h"
#include "sane/sanei_usb.h"
#include "sane/sanei_wire.h"
#include "sane/sanei_codec_bin.h"
#define BACKEND_NAME canondr
#define DEBUG_DECLARE_ONLY
#include "sane/sanei_backend.h"
#include "sane/sanei_config.h"
#include "Canon_DR.h"
```

---

### Post by X-RED_Tech on 2016-04-13
This driver [http://www.canon-europe.com/support/products/document-scanners/dr-series/imageformula-dr-c225.aspx?type=drivers&language=EN&os=Linux%20(64-bit)](http://www.canon-europe.com/support/products/document-scanners/dr-series/imageformula-dr-c225.aspx?type=drivers&language=EN&os=Linux%20(64-bit)) contain a .deb file. That's all you need.

---

