---
title: "filesystem check fails"
date: 2008-07-24
forum: General Help
---

### Post by hammeraxe on 2008-07-24
when my xubuntu 8.04 boots up it now for some reason starts a filesystem check. i goes well until it gets to one of my harddisks. 
this is the output:
```

Log of fsck -C3 -R -A -a 
Thu Jul 24 20:42:40 2008

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 97690 files, 1197066/1252844 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Long filename fragment ":07x:02N:3F-:07-:06a" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (00 vs. expected 5e).
  Not auto-correcting this.
Start cluster field in VFAT long filename slot is not 0 (but 0xff00).
Auto-setting to 0.
Long filename fragment ":08F:0CF:0GF:0KF:0y6:0y7:0y4:0y8:0y9:0yA:0yB:0y8" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x06).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f0a).
Auto-setting to 0.
Long filename fragment ":0qF:0uF:0qF:0mF:0yF:0yH:0yI:0yH:0yG:0yJ:0yK:0yM:0yM" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x10).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f15).
Auto-setting to 0.
Long filename fragment ":1GF:1WF:1aF:1eF:1eF:0yO:0yS:0yT:0yU:0yT:0yS:0yW:0yX" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x1b).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f1f).
Auto-setting to 0.
Long filename fragment ":24F:20F:2CF:2GF:2KF:0yc:0yd:0ya:0ye:0yf:0yg:0yh:0ye" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x26).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2a).
Auto-setting to 0.
Long filename fragment ":2qF:2uF:2qF:2mF:2yF:0yn:0yo:0yo:0yp:0ym:0yq:0ys:0ys" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x30).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f35).
Auto-setting to 0.
Long filename fragment ":3GF:3WF:3aF:3eF:3iF:0yv:0yy:0yz:0y+:0y-:0y+:0z0:0z1" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 5e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x3a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f3d).
Auto-setting to 0.
Reserved field in VFAT long filename slot is not 0 (but 0x46).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x50).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f55).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x58).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5c).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x66).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6a).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x70).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f75).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x7a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f7c).
Auto-setting to 0.
Unexpected long filename sequence number (2 vs. expected 22).
  It could be that just the number is wrong
  if ":88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B" seems to match ":7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x86).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f89).
Auto-setting to 0.
Unexpected long filename sequence number (12 vs. expected 21).
  It could be that just the number is wrong
  if ":8qF:8uF:8qF:8mF:8yF:0+H:0+I:0+I:0+J:0+G:0+K:0+M:0+N" seems to match ":88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B:7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x90).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f95).
Auto-setting to 0.
Unexpected long filename sequence number (22 vs. expected 20).
  It could be that just the number is wrong
  if ":9KF:9WF:9aF:9eF:9eF:0+O:0+S:0+T:0+U:0+T:0+S:0+W:0+X" seems to match ":8qF:8uF:8qF:8mF:8yF:0+H:0+I:0+I:0+J:0+G:0+K:0+M:0+N:88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B:7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x9b).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f9f).
Auto-setting to 0.
Unexpected long filename sequence number (2 vs. expected 19).
  It could be that just the number is wrong
  if ":A8F:ACF:A0F:AGF:AKF:0+b:0+a:0+d:0+e:0+f:0+g:0+h:0+e" seems to match ":9KF:9WF:9aF:9eF:9eF:0+O:0+S:0+T:0+U:0+T:0+S:0+W:0+X:8qF:8uF:8qF:8mF:8yF:0+H:0+I:0+I:0+J:0+G:0+K:0+M:0+N:88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B:7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa6).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0faa).
Auto-setting to 0.
Unexpected long filename sequence number (12 vs. expected 18).
  It could be that just the number is wrong
  if ":AqF:AuF:AqF:AmF:AyF:0+n:0+o:0+o:0+p:0+m:0+q:0+s:0+r" seems to match ":A8F:ACF:A0F:AGF:AKF:0+b:0+a:0+d:0+e:0+f:0+g:0+h:0+e:9KF:9WF:9aF:9eF:9eF:0+O:0+S:0+T:0+U:0+T:0+S:0+W:0+X:8qF:8uF:8qF:8mF:8yF:0+H:0+I:0+I:0+J:0+G:0+K:0+M:0+N:88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B:7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fb5).
Auto-setting to 0.
Unexpected long filename sequence number (20 vs. expected 17).
  It could be that just the number is wrong
  if ":BSF:BWF:BaF:BeF:BaF:0+x:0+y:0+z:0++:0++:0+-:0-0:0-1" seems to match ":AqF:AuF:AqF:AmF:AyF:0+n:0+o:0+o:0+p:0+m:0+q:0+s:0+r:A8F:ACF:A0F:AGF:AKF:0+b:0+a:0+d:0+e:0+f:0+g:0+h:0+e:9KF:9WF:9aF:9eF:9eF:0+O:0+S:0+T:0+U:0+T:0+S:0+W:0+X:8qF:8uF:8qF:8mF:8yF:0+H:0+I:0+I:0+J:0+G:0+K:0+M:0+N:88F:8CF:80F:8GF:8KF:0+5:0+4:0+7:0+8:0+9:0+A:0+8:0+B:7GF:7WF:7aF:7eF:7iF:0zv:0zy:0zz:0z+:0z+:0z-:0+0:0+1".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb8).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbc).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc6).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fca).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fd5).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd8).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fdc).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xe6).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fe9).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xf0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff5).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xfb).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ffc).
Auto-setting to 0.
Unfinished long file name ":FGF:FWF:FaF:FeF:FeF:0-u:0-y:0-z:0-+:0-+:0--:100:101".
  (Start may have been overwritten by \002\020\003\020\004\020\005\020.\006\020\007)
  Not auto-correcting this.
Wrong checksum for long file name ":FGF:FWF:FaF:FeF:FeF:0-u:0-y:0-z:0-+:0-+:0--:100:101".
  (Short name \002\020\003\020\004\020\005\020.\006\020\007 may have changed without updating the long name)
  Not auto-correcting this.
Long filename fragment ":1yF" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (15 vs. expected 0f).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x04).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x220b).
Auto-setting to 0.
Long filename fragment "ø:3d1ÿ:07+Ž:EOo:F0C:440:Fy0:Fy0:Fu3:Fy0:Fu0" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (ff vs. expected 0f).
  Not auto-correcting this.
Start cluster field in VFAT long filename slot is not 0 (but 0xff00).
Auto-setting to 0.
Long filename fragment ":0OF:0SF:0SF:0WF:0KF:0yA:0yB:0yC:0yB:0yA:0yD:0yF:0yF" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x09).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f0e).
Auto-setting to 0.
Long filename fragment ":0qF:14F:18F:1CF:1GF:0yI:0yL:0yM:0yN:0yN:0yO:0yP:0yQ" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x13).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f15).
Auto-setting to 0.
Long filename fragment ":1iF:1mF:1aF:1qF:1uF:0yV:0yW:0yT:0yX:0yY:0yZ:0yZ:0yY" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x1f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f24).
Auto-setting to 0.
Long filename fragment ":2OF:2SF:2SF:2WF:2KF:0yg:0yh:0yg:0yf:0yi:0yj:0yl:0ym" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x29).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2e).


Auto-setting to 0.
Long filename fragment ":2uF:34F:38F:3CF:3GF:0yo:0yr:0ys:0yt:0yt:0yu:0yv:0yw" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x33).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f35).
Auto-setting to 0.
Long filename fragment ":3iF:3mF:3aF:3qF:3uF:0y-:0z0:0yz:0z1:0z2:0z3:0z4:0z1" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x3f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f43).
Auto-setting to 0.
Reserved field in VFAT long filename slot is not 0 (but 0x49).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4e).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x51).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f55).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x5f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f63).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x69).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6e).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x73).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f78).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x7f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f84).
Auto-setting to 0.
Unexpected long filename sequence number (5 vs. expected 26).
  It could be that just the number is wrong
  if ":8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G" seems to match ":7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x89).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8e).
Auto-setting to 0.
Unexpected long filename sequence number (15 vs. expected 25).
  It could be that just the number is wrong
  if ":8uF:94F:98F:9CF:98F:0+K:0+L:0+M:0+N:0+N:0+O:0+P:0+Q" seems to match ":8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G:7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x91).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f95).
Auto-setting to 0.
Unexpected long filename sequence number (27 vs. expected 24).
  It could be that just the number is wrong
  if ":9iF:9mF:9aF:9qF:9uF:0+V:0+W:0+T:0+X:0+Y:0+Z:0+X:0+a" seems to match ":8uF:94F:98F:9CF:98F:0+K:0+L:0+M:0+N:0+N:0+O:0+P:0+Q:8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G:7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x9f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fa2).
Auto-setting to 0.
Unexpected long filename sequence number (5 vs. expected 23).
  It could be that just the number is wrong
  if ":AOF:ASF:ASF:AWF:AKF:0+g:0+h:0+h:0+i:0+f:0+j:0+l:0+k" seems to match ":9iF:9mF:9aF:9qF:9uF:0+V:0+W:0+T:0+X:0+Y:0+Z:0+X:0+a:8uF:94F:98F:9CF:98F:0+K:0+L:0+M:0+N:0+N:0+O:0+P:0+Q:8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G:7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa9).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fae).
Auto-setting to 0.
Unexpected long filename sequence number (13 vs. expected 22).
  It could be that just the number is wrong
  if ":B0F:B4F:B8F:BCF:B8F:0+q:0+r:0+s:0+t:0+u:0+t:0+v:0+w" seems to match ":AOF:ASF:ASF:AWF:AKF:0+g:0+h:0+h:0+i:0+f:0+j:0+l:0+k:9iF:9mF:9aF:9qF:9uF:0+V:0+W:0+T:0+X:0+Y:0+Z:0+X:0+a:8uF:94F:98F:9CF:98F:0+K:0+L:0+M:0+N:0+N:0+O:0+P:0+Q:8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G:7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb1).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fb6).
Auto-setting to 0.
Unexpected long filename sequence number (27 vs. expected 21).
  It could be that just the number is wrong
  if ":BeF:BaF:BmF:BqF:BuF:0+-:0-0:0+z:0-1:0-2:0-3:0-1:0-4" seems to match ":B0F:B4F:B8F:BCF:B8F:0+q:0+r:0+s:0+t:0+u:0+t:0+v:0+w:AOF:ASF:ASF:AWF:AKF:0+g:0+h:0+h:0+i:0+f:0+j:0+l:0+k:9iF:9mF:9aF:9qF:9uF:0+V:0+W:0+T:0+X:0+Y:0+Z:0+X:0+a:8uF:94F:98F:9CF:98F:0+K:0+L:0+M:0+N:0+N:0+O:0+P:0+Q:8OF:8SF:8SF:8WF:8KF:0+A:0+B:0+B:0+C:0+9:0+D:0+F:0+G:7eF:7aF:7mF:7qF:7uF:0z-:0+0:0zz:0+1:0+2:0+3:0+3:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xbf).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fc2).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc9).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fce).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd3).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fd5).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xdf).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fe3).
Auto-setting to 0.
Orphaned long file name part ":DeF:DaF:DmF:DqF:DuF:0-V:0-W:0-T:0-X:0-Y:0-Z:0-a:0-X"
  Auto-deleting.
Reserved field in VFAT long filename slot is not 0 (but 0xf1).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff5).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xff).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x1002).
Auto-setting to 0.
Unfinished long file name ":FiF:FmF:FaF:FqF:FuF:0-+:0-z:100:101:102:103:101:104".
  (Start may have been overwritten by \005\020\006\020\007\020\006\020.\005\020\010)
  Not auto-correcting this.
Wrong checksum for long file name ":FiF:FmF:FaF:FqF:FuF:0-+:0-z:100:101:102:103:101:104".
  (Short name \005\020\006\020\007\020\006\020.\005\020\010 may have changed without updating the long name)
  Not auto-correcting this.
Long filename fragment ":0SF:0OF:0KF:0WF:0OF:0y9:0yA:0yB:0yC:0xn:0xo:0xr:0xs" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x08).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0eee).
Auto-setting to 0.
Long filename fragment ":18F:14F:1CF:1GF:1KF:0yN:0yO:0yP:0yQ:0yR:0yV:0yQ:0yS" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x16).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f1b).
Auto-setting to 0.
Long filename fragment ":3eF:3iF:3OF:3iF:3mF:0yz:0yx:0yc:0yd:0ye:0yZ:0yj:0yd" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x3a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2c).
Auto-setting to 0.
Long filename fragment ":2iF:2SF:2uF:2eF:3uF:0z0:0z1:0y+:0z0:0z0:0z2:0z0:0z3" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x3f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f41).
Auto-setting to 0.
Reserved field in VFAT long filename slot is not 0 (but 0x49).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x30).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f30).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x57).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5c).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x5d).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5f).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x6e).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6e).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x63).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f72).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x66).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f76).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x7c).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f81).
Auto-setting to 0.
Unexpected long filename sequence number (3 vs. expected 22).
  It could be that just the number is wrong
  if ":8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A" seems to match ":7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x87).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8c).
Auto-setting to 0.
Unexpected long filename sequence number (13 vs. expected 21).
  It could be that just the number is wrong
  if ":8uF:8yF:90F:8yF:8uF:0+I:0+J:0+K:0+J:0+I:0+L:0+N:0+O" seems to match ":8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A:7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x91).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f96).
Auto-setting to 0.
Unexpected long filename sequence number (23 vs. expected 20).
  It could be that just the number is wrong
  if ":9OF:9aF:9eF:9iF:9mF:0+T:0+Q:0+U:0+V:0+W:0+W:0+U:0+Y" seems to match ":8uF:8yF:90F:8yF:8uF:0+I:0+J:0+K:0+J:0+I:0+L:0+N:0+O:8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A:7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x9c).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fa1).
Auto-setting to 0.
Unexpected long filename sequence number (3 vs. expected 19).
  It could be that just the number is wrong
  if ":AGF:ACF:A8F:AKF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j" seems to match ":9OF:9aF:9eF:9iF:9mF:0+T:0+Q:0+U:0+V:0+W:0+W:0+U:0+Y:8uF:8yF:90F:8yF:8uF:0+I:0+J:0+K:0+J:0+I:0+L:0+N:0+O:8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A:7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa7).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fac).
Auto-setting to 0.
Unexpected long filename sequence number (10 vs. expected 18).
  It could be that just the number is wrong
  if ":AuF:AyF:B0F:AyF:AuF:0+o:0+p:0+q:0+q:0+r:0+o:0+t:0+u" seems to match ":AGF:ACF:A8F:AKF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9OF:9aF:9eF:9iF:9mF:0+T:0+Q:0+U:0+V:0+W:0+W:0+U:0+Y:8uF:8yF:90F:8yF:8uF:0+I:0+J:0+K:0+J:0+I:0+L:0+N:0+O:8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A:7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb1).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fb6).
Auto-setting to 0.
Unexpected long filename sequence number (23 vs. expected 17).
  It could be that just the number is wrong
  if ":BOF:BaF:BeF:BiF:BmF:0+w:0+z:0++:0+-:0-0:0-1:0++:0-2" seems to match ":AuF:AyF:B0F:AyF:AuF:0+o:0+p:0+q:0+q:0+r:0+o:0+t:0+u:AGF:ACF:A8F:AKF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9OF:9aF:9eF:9iF:9mF:0+T:0+Q:0+U:0+V:0+W:0+W:0+U:0+Y:8uF:8yF:90F:8yF:8uF:0+I:0+J:0+K:0+J:0+I:0+L:0+N:0+O:8GF:8GF:8KF:88F:8OF:0+8:0+8:0+9:0+6:0+A:0+B:0+B:0+A:7aF:7WF:7eF:7iF:7mF:0zx:0zz:0z+:0z-:0+0:0+0:0z+:0+2".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xbb).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbf).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc7).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fcc).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fd6).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xdb).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fdf).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xe7).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fec).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xf0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff6).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xfc).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x1000).
Auto-setting to 0.
Unfinished long file name ":FaF:FOF:FeF:FiF:FmF:0-z:0-w:0-+:0--:100:0-+:101:102".
  (Start may have been overwritten by \003\020\004\020\003\020\005\020.\006\020\007)
  Not auto-correcting this.
Wrong checksum for long file name ":FaF:FOF:FeF:FiF:FmF:0-z:0-w:0-+:0--:100:0-+:101:102".
  (Short name \003\020\004\020\003\020\005\020.\006\020\007 may have changed without updating the long name)
  Not auto-correcting this.
Long filename fragment ":0i7:0KD:4ar:1zx:2SZÿ:080:1yb:1Cw:0a6" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (09 vs. expected 0f).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x12).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0d17).
Auto-setting to 0.
Long filename fragment ":0G1:3r2:2Ta:24i:1SL:080:5bW:3h-:34-:2CV:0qM:69f:47-" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (00 vs. expected 0f).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x09).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0100).
Auto-setting to 0.
Long filename fragment ":08F:0KF:0GF:0OF:0WF:0yA:0yA:0y9:0yB:0yA:0yB:0yC:0yB" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x09).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f0c).
Auto-setting to 0.
Long filename fragment ":0qF:0uF:0mF:0yF:0uF:0yB:0yG:0yD:0yG:0yB:0yH:0yI:0yG" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x0d).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f11).
Auto-setting to 0.
Long filename fragment ":14F:1CF:0CF:08F:0SF:0xt:0xs:0yK:0yL:0yM:0yO:0yQ:0yQ" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0e vs. expected 0f).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xf9).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f19).
Auto-setting to 0.
Long filename fragment ":1WF:1iF:1eF:1mF:2GF:0yc:0yb:0ya:0yd:0ye:0yf:0yf:0ye" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x25).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2a).
Auto-setting to 0.
Long filename fragment ":2mF:2aF:2iF:1OF:1KF:0yj:0yf:0yi:0yk:0yl:0ym:0yl:0yk" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x17).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f31).
Auto-setting to 0.
Long filename fragment ":1WF:2CF:1qF:1uF:1yF:0yp:0yq:0yp:0yo:0yr:0yr:0yp:0yt" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x32).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f36).
Auto-setting to 0.
Long filename fragment ":3aF:3aF:3eF:3SF:3eF:0yx:0yy:0yz:0y+:0y+:0yz:0yY:0yU" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x39).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f3f).
Auto-setting to 0.
Long filename fragment ":24F:1uF:20F:40F:44F:0z3:0z1:0z0:0yU:0yT:0yW:0z5:0z6" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x42).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f44).
Auto-setting to 0.
Reserved field in VFAT long filename slot is not 0 (but 0x46).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x44).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4e).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x4f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f54).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x59).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x63).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5a).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x68).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x67).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6f).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x70).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f74).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x78).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f80).
Auto-setting to 0.
Unexpected long filename sequence number (1 vs. expected 17).
  It could be that just the number is wrong
  if ":80F:7uF:8GF:8KF:8OF:0+4:0+6:0zs:0zt:0zp:0zp:0zs:0+2" seems to match ":7WF:7aF:7eF:7eF:7iF:0zy:0zz:0z+:0z+:0z-:0zy:0z-:0z+".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x87).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f72).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x89).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8c).
Auto-setting to 0.
Unexpected long filename sequence number (20 vs. expected 30).
  It could be that just the number is wrong
  if ":9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q" seems to match ":8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x95).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f98).
Auto-setting to 0.
Unexpected long filename sequence number (26 vs. expected 29).
  It could be that just the number is wrong
  if ":9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S" seems to match ":9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa4).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8c).
Auto-setting to 0.
Unexpected long filename sequence number (29 vs. expected 28).
  It could be that just the number is wrong
  if ":9uF:9uF:9yF:9mF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j" seems to match ":9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S:9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa7).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fac).
Auto-setting to 0.
Unexpected long filename sequence number (10 vs. expected 27).
  It could be that just the number is wrong
  if ":AuF:AqF:AmF:AyF:AuF:0+m:0+n:0+o:0+p:0+m:0+o:0+X:0+T" seems to match ":9uF:9uF:9yF:9mF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S:9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xac).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fa0).
Auto-setting to 0.
Unexpected long filename sequence number (29 vs. expected 26).
  It could be that just the number is wrong
  if ":9mF:A0F:BGF:BKF:BOF:0+t:0+s:0+u:0+v:0+w:0+w:0+u:0++" seems to match ":AuF:AqF:AmF:AyF:AuF:0+m:0+n:0+o:0+p:0+m:0+o:0+X:0+T:9uF:9uF:9yF:9mF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S:9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb5).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbf).
Auto-setting to 0.
Unexpected long filename sequence number (31 vs. expected 25).
  It could be that just the number is wrong
  if ":BeF:BuF:BmF:ByF:BqF:0++:0+v:0+y:0+z:0+y:0+v:0+x:0-3" seems to match ":9mF:A0F:BGF:BKF:BOF:0+t:0+s:0+u:0+v:0+w:0+w:0+u:0++:AuF:AqF:AmF:AyF:AuF:0+m:0+n:0+o:0+p:0+m:0+o:0+X:0+T:9uF:9uF:9yF:9mF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S:9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xbc).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbb).
Auto-setting to 0.
Unexpected long filename sequence number (28 vs. expected 24).
  It could be that just the number is wrong
  if ":CCF:BiF:C8F:C8F:C4F:0-1:0-2:0-0:0-0:0+-:0-1:0-0:0+u" seems to match ":BeF:BuF:BmF:ByF:BqF:0++:0+v:0+y:0+z:0+y:0+v:0+x:0-3:9mF:A0F:BGF:BKF:BOF:0+t:0+s:0+u:0+v:0+w:0+w:0+u:0++:AuF:AqF:AmF:AyF:AuF:0+m:0+n:0+o:0+p:0+m:0+o:0+X:0+T:9uF:9uF:9yF:9mF:AOF:0+e:0+e:0+f:0+c:0+g:0+h:0+i:0+j:9iF:9WF:A8F:ACF:AGF:0+b:0+Y:0+G:0+H:0+D:0+D:0+G:0+S:9CF:9KF:9GF:9CF:9OF:0+M:0+N:0+L:0+9:0+B:0+A:0+P:0+Q:8CF:7yF:80F:8CF:8WF:0+A:0+C:0+D:0+E:0+E:0+F:0+I:0+J".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc3).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbf).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc7).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fcb).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fcf).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd5).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fd6).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xe6).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fea).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xed).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff2).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xde).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fe4).
Auto-setting to 0.
Orphaned long file name part ":DuF:DyF:DiF:DiF:DeF:0-W:0-X:0-Y:0-Y:0-Z:0-W:0-Z:0-Y"
  Auto-deleting.
Reserved field in VFAT long filename slot is not 0 (but 0xff).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f05).
Auto-setting to 0.
Unexpected long filename sequence number (8 vs. expected 26).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x0c).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f11).
Auto-setting to 0.
Unexpected long filename sequence number (18 vs. expected 25).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x16).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f1b).
Auto-setting to 0.
Unexpected long filename sequence number (27 vs. expected 24).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x21).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f25).
Auto-setting to 0.
Unexpected long filename sequence number (9 vs. expected 23).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x27).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f26).
Auto-setting to 0.
Unexpected long filename sequence number (10 vs. expected 22).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x2a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2f).
Auto-setting to 0.
Unexpected long filename sequence number (15 vs. expected 21).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x2b).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f35).
Auto-setting to 0.
Unexpected long filename sequence number (24 vs. expected 20).
  Not auto-correcting this.
Checksum in long filename part wrong (0f vs. expected 0e).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x39).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f3d).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x42).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f42).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x46).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f49).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x50).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f52).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x58).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f59).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x5c).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5e).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x66).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6a).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x6e).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f71).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x75).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f77).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x78).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f7e).
Auto-setting to 0.
Unexpected long filename sequence number (0 vs. expected 21).
  It could be that just the number is wrong
  if ":84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5" seems to match ":7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x84).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f85).
Auto-setting to 0.
Unexpected long filename sequence number (6 vs. expected 20).
  It could be that just the number is wrong
  if ":8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A" seems to match ":84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x89).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8a).
Auto-setting to 0.
Unexpected long filename sequence number (11 vs. expected 19).
  It could be that just the number is wrong
  if ":8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J" seems to match ":8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x90).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f91).
Auto-setting to 0.
Unexpected long filename sequence number (20 vs. expected 18).
  It could be that just the number is wrong
  if ":9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O" seems to match ":8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x98).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f98).
Auto-setting to 0.
Unexpected long filename sequence number (28 vs. expected 17).
  It could be that just the number is wrong
  if ":9qF:9uF:9qF:9mF:9qF:0+V:0+W:0+V:0+U:0+U:0+X:0+Y:0+W" seems to match ":9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O:8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x9e).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fa0).
Auto-setting to 0.
Unexpected long filename sequence number (1 vs. expected 16).
  It could be that just the number is wrong
  if ":A4F:ACF:A8F:AKF:A8F:0+Z:0+a:0+b:0+c:0+d:0+e:0+c:0+f" seems to match ":9qF:9uF:9qF:9mF:9qF:0+V:0+W:0+V:0+U:0+U:0+X:0+Y:0+W:9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O:8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xa3).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fa7).
Auto-setting to 0.
Unexpected long filename sequence number (10 vs. expected 15).
  It could be that just the number is wrong
  if ":AaF:AOF:AaF:AeF:AiF:0+j:0+k:0+k:0+l:0+i:0+m:0+o:0+n" seems to match ":A4F:ACF:A8F:AKF:A8F:0+Z:0+a:0+b:0+c:0+d:0+e:0+c:0+f:9qF:9uF:9qF:9mF:9qF:0+V:0+W:0+V:0+U:0+U:0+X:0+Y:0+W:9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O:8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xac).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fb1).
Auto-setting to 0.
Unexpected long filename sequence number (16 vs. expected 14).
  It could be that just the number is wrong
  if ":BCF:BGF:BCF:B0F:BCF:0+r:0+s:0+t:0+u:0+u:0+v:0+x:0+w" seems to match ":AaF:AOF:AaF:AeF:AiF:0+j:0+k:0+k:0+l:0+i:0+m:0+o:0+n:A4F:ACF:A8F:AKF:A8F:0+Z:0+a:0+b:0+c:0+d:0+e:0+c:0+f:9qF:9uF:9qF:9mF:9qF:0+V:0+W:0+V:0+U:0+U:0+X:0+Y:0+W:9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O:8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xb4).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fb6).
Auto-setting to 0.
Unexpected long filename sequence number (29 vs. expected 13).
  It could be that just the number is wrong
  if ":BeF:BiF:BmF:BuF:BmF:0+y:0++:0+-:0-0:0+-:0++:0-1:0-0" seems to match ":BCF:BGF:BCF:B0F:BCF:0+r:0+s:0+t:0+u:0+u:0+v:0+x:0+w:AaF:AOF:AaF:AeF:AiF:0+j:0+k:0+k:0+l:0+i:0+m:0+o:0+n:A4F:ACF:A8F:AKF:A8F:0+Z:0+a:0+b:0+c:0+d:0+e:0+c:0+f:9qF:9uF:9qF:9mF:9qF:0+V:0+W:0+V:0+U:0+U:0+X:0+Y:0+W:9KF:9OF:9OF:9SF:9GF:0+P:0+Q:0+Q:0+R:0+O:0+S:0+R:0+O:8iF:8mF:8qF:8uF:8yF:0+F:0+E:0+H:0+I:0+H:0+E:0+I:0+J:8SF:8WF:8SF:8OF:8OF:0+8:0+A:0+8:0+9:0+9:0+B:0+D:0+A:84F:88F:88F:8CF:80F:0+0:0+3:0+0:0+4:0+5:0+6:0+4:0+5:7SF:7WF:7aF:7eF:7aF:0zv:0zw:0zx:0zy:0zz:0z+:0z-:0zy".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xbb).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fbe).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xc5).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fc7).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xcd).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fcf).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xd0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fd8).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xdc).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fdd).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xe3).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0fe7).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xe8).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0feb).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xf0).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff3).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xf6).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0ff8).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xfc).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x1000).
Auto-setting to 0.
Unfinished long file name ":FqF:FmF:FyF:FyG:0--:100:101:102:101:100:103:102".
  (Start may have been overwritten by \004\020\002\020\003\020\003\020.\005\020\004)
  Not auto-correcting this.
Wrong checksum for long file name ":FqF:FmF:FyF:FyG:0--:100:101:102:101:100:103:102".
  (Short name \004\020\002\020\003\020\003\020.\005\020\004 may have changed without updating the long name)
  Not auto-correcting this.
Long filename fragment ":0K9:0iJ:0KB:143:0G7:2Ky:1af:0yN" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (0b vs. expected 0f).
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x15).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0b04).
Auto-setting to 0.
Long filename fragment ":0C0:6q0Í:Eu0:07-" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (ff vs. expected 0f).
  Not auto-correcting this.
Start cluster field in VFAT long filename slot is not 0 (but 0xfe90).
Auto-setting to 0.
Long filename fragment ":0K0:200Î:0S0:07s" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Checksum in long filename part wrong (ff vs. expected 0f).
  Not auto-correcting this.
Start cluster field in VFAT long filename slot is not 0 (but 0xfe90).
Auto-setting to 0.
Long filename fragment ":0aF:0OF:0KF:0aF:0eF:0yB:0yA:0y9:0yC:0yD:0yE:0yF:0yC" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x06).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f0e).
Auto-setting to 0.
Long filename fragment ":0yF:0uF:10F:14F:0yF:0yC:0yI:0yI:0yJ:0yD:0yK:0yM:0yL" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x0d).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f15).
Auto-setting to 0.
Long filename fragment ":1SF:1SF:1WF:1KF:1WF:0yP:0yP:0yQ:0yO:0yQ:0yP:0yZ:0ya" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x17).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f1b).
Auto-setting to 0.
Long filename fragment ":28F:24F:2CF:24F:28F:0yV:0yU:0yX:0yU:0yV:0yS:0yT:0yU" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x1f).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f1c).
Auto-setting to 0.
Long filename fragment ":20F:1qF:2KF:2OF:2SF:0yb:0ye:0yg:0yh:0yi:0yi:0yg:0yk" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x26).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f2d).
Auto-setting to 0.
Long filename fragment ":2qF:2yF:30F:34F:34F:0yl:0yp:0yq:0yr:0yr:0ys:0yc:0yf" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x32).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f33).
Auto-setting to 0.
Long filename fragment ":3SF:3WF:3aF:3aF:3eF:0yw:0yx:0yt:0yy:0yt:0yx:0yz:0yy" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x37).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f3b).
Auto-setting to 0.
Long filename fragment ":3mF:3qF:3qF:3uF:3yF:0z1:0z2:0z2:0z3:0z0:0z2:0z3:0z4" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x40).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f44).
Auto-setting to 0.
Reserved field in VFAT long filename slot is not 0 (but 0x45).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f4b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x4d).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f55).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x5c).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f5b).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x6d).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f70).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x5a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f6f).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x78).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f79).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x62).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f64).
Auto-setting to 0.
A new long file name starts within an old one.
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x67).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f81).
Auto-setting to 0.
Unexpected long filename sequence number (2 vs. expected 4).
  It could be that just the number is wrong
  if ":80F:84F:8CF:8GF:8KF:0+6:0+3:0+7:0+3:0+6:0+6:0+7:0+9" seems to match ":6SF:6KF:6OF:6OF:6WF:0zz:0z+:0z-:0+0:0z+:0zz:0+0:0zz".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x85).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f88).
Auto-setting to 0.
Unexpected long filename sequence number (7 vs. expected 3).
  It could be that just the number is wrong
  if ":8WF:8WF:8eF:8aF:7uF:0+C:0z+:0+C:0z-:0z-:0+C:0z-:0+D" seems to match ":80F:84F:8CF:8GF:8KF:0+6:0+3:0+7:0+3:0+6:0+6:0+7:0+9:6SF:6KF:6OF:6OF:6WF:0zz:0z+:0z-:0+0:0z+:0zz:0+0:0zz".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x8b).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f8d).
Auto-setting to 0.
Unexpected long filename sequence number (14 vs. expected 2).
  It could be that just the number is wrong
  if ":8yF:90F:94F:98F:8yF:0+H:0+J:0+I:0+J:0+K:0+I:0+M:0+N" seems to match ":8WF:8WF:8eF:8aF:7uF:0+C:0z+:0+C:0z-:0z-:0+C:0z-:0+D:80F:84F:8CF:8GF:8KF:0+6:0+3:0+7:0+3:0+6:0+6:0+7:0+9:6SF:6KF:6OF:6OF:6WF:0zz:0z+:0z-:0+0:0z+:0zz:0+0:0zz".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x91).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0f95).
Auto-setting to 0.
Unexpected long filename sequence number (23 vs. expected 1).
  It could be that just the number is wrong
  if ":9WF:9KF:9aF:94F:90F:0+P:0+G:0+R:0+S:0+T:0+T:0+R:0+V" seems to match ":8yF:90F:94F:98F:8yF:0+H:0+J:0+I:0+J:0+K:0+I:0+M:0+N:8WF:8WF:8eF:8aF:7uF:0+C:0z+:0+C:0z-:0z-:0+C:0z-:0+D:80F:84F:8CF:8GF:8KF:0+6:0+3:0+7:0+3:0+6:0+6:0+7:0+9:6SF:6KF:6OF:6OF:6WF:0zz:0z+:0z-:0+0:0z+:0zz:0+0:0zz".
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0x9a).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x0Warning... fsck.vfat for device /dev/sdb5 exited with signal 11.
fsck died with exit status 8

Thu Jul 24 20:43:49 2008
----------------


```

after that it says i have to manually repair the filesystem and enters a console of which i exit and continue normal boot. yet my harddisk is not mounted

these are the relevant fstab lines:
```

/dev/sdb1       /media/win98_C  auto    noauto,user,rw        0       2
/dev/sdb5       /media/win98_D  auto    noauto,user,rw        0       2

```

do you have any ideas on how to fix this? :confused:

---

### Post by aaronb on 2008-07-24
FAT32 file system are not very fault resistant as say ext3 or NTFS.

May I ask why your using FAT32? (eg Windows install or Sharing files between Linux and Windows).

---

### Post by hammeraxe on 2008-07-24
there is an old win98. its bootable i guess but i dont have dual boot set up. and then there is some data that i need (find useful / dont want to lose)

---

### Post by aaronb on 2008-07-24
I think before any further attempt to fix the FAT32 file system, a backup of the important data in case it gets lost would be prudent (On all partitions).

You could try running scandisk from Windows or DOS to see if its able to fix the errors that fsck can not.

---

### Post by plucky on 2008-07-24
```
/dev/sdb1       /media/win98_C  auto    noauto,user,rw        0       2
/dev/sdb5       /media/win98_D  auto    noauto,user,rw        0       2
```


I don't think these entries in Fstab are correct.
As the partition is fat32,you don't want fsck to run a file system check so you need to set the lines in fstab to
```
/dev/sdb1       /media/win98_C  auto    noauto,user,rw        0       0
/dev/sdb5       /media/win98_D  auto    noauto,user,rw        0       0
```

i.e change the 2 to a 0 will stop the file system check.


see this link for [Mounting Fat32 partitions](http://www.psychocats.net/ubuntu/mountwindows#fat32)


Good Luck

---

### Post by hammeraxe on 2008-07-25
thanks plucky

i had no idea what those numbers stood for so i just copied them from an entry of another harddisk
I'll test this when i get home

---

