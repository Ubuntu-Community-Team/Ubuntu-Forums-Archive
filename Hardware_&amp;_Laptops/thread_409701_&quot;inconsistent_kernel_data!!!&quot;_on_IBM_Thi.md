---
title: "&quot;inconsistent kernel data!!!&quot; on IBM Thinkpad"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by damgaard on 2007-04-14
Hi

I am using Edgy on an IBM Thinkpad T42.
I get these errors/warnings in my dmesg:
[17335717.752000] [fglrx:firegl_rmmap] *ERROR* map 0xd85af450 still in use (map_count=1), force it to be removed anyway
[17335717.764000] [fglrx:firegl_rmmap] *ERROR* map 0xf35fcc50 still in use (map_count=1)
[17335717.764000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf35fcc40 still mapped (user_handle = 0x00227000)
[17335717.968000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17358398.180000] [fglrx:firegl_rmmap] *ERROR* map 0xd24d1250 still in use (map_count=1)
[17358398.180000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xd24d1240 still mapped (user_handle = 0x00234000)
[17358398.180000] [fglrx:firegl_rmmap] *ERROR* map 0xd24d1250 still in use (map_count=1), force it to be removed anyway
[17358398.184000] [fglrx:firegl_rmmap] *ERROR* map 0xd24d13d0 still in use (map_count=1)
[17358398.184000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xd24d13c0 still mapped (user_handle = 0x00231000)
[17358398.500000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!

Do you have any idea whats wrong or how to fix it?


PS.
I would attach the full dmesg from my laptop, but I really tried... First I did a dmesg > ~/tmp/dmesg, then I couldn't upload that file, because it said "invalid file". Then I renamed it to dmesg.log. Then I *still* could not upload it. Then I renamed it to dmesg.txt then it was too big. Then I just gave up. How restrictive must this forum be?! And WTF is the point of blocking files by extensions? And the size? A text file of ~80kb is too large?! Come on!

---

### Post by damgaard on 2007-04-14
The full dmesg is available here: [http://thomasdamgaard.dk/p/?paste=493](http://thomasdamgaard.dk/p/?paste=493).

---

