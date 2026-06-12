---
title: "Problem with printer installation (Konica Bizhub 250)"
date: 2014-02-14
forum: Hardware
---

### Post by WimiBuntu on 2014-02-14
Dear all 

I tried to install the Konic Bizhub 250 according to the instructions from the manufacturer's manual. However, I still see a red button with an exclamation mark at the corner of the printer in the printers overview. The status message in the ink/toner section says "cups insecure filter". So I googled for that and changed the permissions of /usr/lib/cups/filter and backend (chown/chgrp) to root. However, the status message remains the same.

Do you have another advice for me?

Best regards

PS: I use Ubuntu 13.10

---

### Post by gifford on 2014-02-14
Maybe this link will help: [http://ubuntuforums.org/showthread.php?t=1530162](http://ubuntuforums.org/showthread.php?t=1530162)

---

### Post by WimiBuntu on 2014-02-15
Thanks, in fact it brought me one step further. It seems I cannot change the permissions on a link in usr lib cups filter, there was a file /usr/lib/kmpu/printutility.filter, for which I had to change the permissions. However, now the status message is gone, but even the test page won't print.

Testing from the Ubuntu printer administration leads to "There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Trying the same under cups leads to "Unsupported format "application/vnd.cups-pdf-banner"."

Do you have further suggestions?

---

### Post by gifford on 2014-02-15
Here is another link that I hope helps.[http://ubuntuforums.org/showthread.php?t=1313291](http://ubuntuforums.org/showthread.php?t=1313291)
Otherwise, this is out of my league.

---

### Post by WimiBuntu on 2014-02-15
Thank you very much. But I already followed the suggestions of that thread and it does not say anything about the other error messages. Still, thanks for your help!

---

