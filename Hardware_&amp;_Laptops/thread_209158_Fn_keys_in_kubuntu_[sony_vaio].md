---
title: "Fn keys in kubuntu [sony vaio]"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by mmc on 2006-07-04
hi all, i've tried searching/googling for this but so far havent found an answer and i was hoping someone here could help/point me in the right direction.

I have kubuntu dapper installed on a sony vaio z1-rsp ... the only Fn keys keys to function correctly are my brightness up/down ( i believe because its invoking /dev/sonypi as opposed to the generic acpi scripts).

/var/log/acpid detects all my funtion keys but i suspect something is out of sync with the SPIC numbers (i've tried changing the major,minor numbers of /dev/sonypi) - interestingly the sucessful sonybright.sh script exists with status 2 :-s ... i've included a snippet of my logs below for info.

Does anyone have any idea what the missing link to get this working in kubuntu could be?

ta
martin.

<snip>
[Tue Jul  4 22:43:57 2006] received event "sony/hotkey SPIC 00000001 00000011"
[Tue Jul  4 22:43:57 2006] notifying client 4078[116:116]
[Tue Jul  4 22:43:57 2006] executing action "/etc/acpi/sonybright.sh up"
[Tue Jul  4 22:43:57 2006] BEGIN HANDLER MESSAGES
[Tue Jul  4 22:43:57 2006] END HANDLER MESSAGES
[Tue Jul  4 22:43:57 2006] action exited with status 2
[Tue Jul  4 22:43:57 2006] completed event "sony/hotkey SPIC 00000001 00000011"
[Tue Jul  4 22:47:28 2006] received event "sony/hotkey SPIC 00000001 0000000f"
[Tue Jul  4 22:47:28 2006] notifying client 4078[116:116]
[Tue Jul  4 22:47:28 2006] executing action "/etc/acpi/volupbtn.sh"
[Tue Jul  4 22:47:28 2006] BEGIN HANDLER MESSAGES
[Tue Jul  4 22:47:28 2006] END HANDLER MESSAGES
[Tue Jul  4 22:47:28 2006] action exited with status 0
[Tue Jul  4 22:47:28 2006] completed event "sony/hotkey SPIC 00000001 0000000f"
</snip>

---

### Post by maikischa on 2006-11-18
Same problem VGN-FE21M

---

