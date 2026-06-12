---
title: "webpage hyperlink"
date: 2008-08-11
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-08-11
my local tv station provides streaming video but it's hyperlink always changes

the source code of [station1]("http://2008.i-cable.com/webapps/live_video/video_live_p2p.php?chid=1")'s site writes:
```

.........
</title>
<LINK href="../css/olympic_re.css" type="text/css" rel="stylesheet">
..........
var WMP_CH2_URL = "http://2008.i-cable.com/asx/2008_live1_1012378.asx"
........., etc  
```

Only this address is important [http://2008.i-cable.com/asx/2008_live1_1012378.asx](http://2008.i-cable.com/asx/2008_live1_1012378.asx) . But this address changes every day. the number 1012378 changes to another. I don't want to visit it's webpage everytime (it's site is slow!) so could anyone tell me how to create a webpage which the hyperlinks would change automatically according the the tv station's site? 

here's my page

```
<p><font size="6"><a href="http://2008.i-cable.com/asx/2008_live1_1012378.asx">station1</a>

<a href="http://2008.i-cable.com/asx/2008_live2_1028547.asx">station2</a>

<a href="http://2008.i-cable.com/asx/2008_delay1_1038746.asx">station3</a>

<a href="http://2008.i-cable.com/asx/2008_delay2_1045874.asx">station4 </a></font></p>
```

could the link [http://2008.i-cable.com/asx/xxxxxxxxxxxxxxxxx.asx](http://2008.i-cable.com/asx/xxxxxxxxxxxxxxxxx.asx) changes accordingly as the official link has changed? 
thanks!

here's the address of the webpage of the stations: [station1]("http://2008.i-cable.com/webapps/live_video/video_live_p2p.php?chid=1") [station2]("http://2008.i-cable.com/webapps/live_video/video_live_p2p.php?chid=2&readyToPlay=&p=") [station3]("http://2008.i-cable.com/webapps/live_video/video_live_p2p.php?chid=3&readyToPlay=&p=") [station4]("http://2008.i-cable.com/webapps/live_video/video_live_p2p.php?chid=4&readyToPlay=&p=")

---

