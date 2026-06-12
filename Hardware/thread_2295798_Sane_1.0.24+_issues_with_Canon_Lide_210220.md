---
title: "Sane 1.0.24+ issues with Canon Lide 210/220"
date: 2015-09-21
forum: Hardware
---

### Post by Vladislav_Fedyushi on 2015-09-21
Hello,
I have a problem with using Canon CanoScan LiDe 210 and 220 with the latest sane versions.
A year ago I've bought Canon 210, and it worked perfectly with sane 1.0.23 both in Ubuntu and OpenSuse. Later, when installed sane 1.0.24, I found that the scanner doesn't function properly. Firstly, scanning speed for 300 dpi (grayscale) increased from about 10 seconds to 15-17 secs. The quality is also very poor, and the picture is highly pixeled. Secondly, when scanning in 600 dpi (also grayscale), the scanner's camera doesn't reach the end and stops nearly at 70%. The picture is extended respectively. But I didn't consider this a problem, because there always was alternative (sane 1.0.23).
Now my Canon LiDe 210 is out, and I've bought 220 which is mainly the same (also, I haven't found a new 210). Unfortunately, it isn't supported by any version of sane except the git one. I've installed the git sane version and found the same problems with speed and quality; but now I can't simply downgrade sane.
Is there any hope to fix this issue? Or should I just return my Canon 220 to the vendor?
Thank you for your attention.

Here are examples: [https://www.dropbox.com/sh/jyou5zb1hhab9gs/AAARKiaaqfWDYxTbKr4fpn4Ka?dl=0](https://www.dropbox.com/sh/jyou5zb1hhab9gs/AAARKiaaqfWDYxTbKr4fpn4Ka?dl=0)
As you can see, scanning in colour mode works OK.

The same problem is described here: [http://sane-devel.alioth.debian.narkive.com/RdYMbPt7/genesys-canon-lide-210-aspect-ratio-problem-at-600-dpi](http://sane-devel.alioth.debian.narkive.com/RdYMbPt7/genesys-canon-lide-210-aspect-ratio-problem-at-600-dpi) , but without any solution.

---

