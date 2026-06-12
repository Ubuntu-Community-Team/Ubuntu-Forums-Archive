---
title: "How to use a perl Script"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by marklodge on 2009-06-20
*(--i've posted this in the Absolute Begginners Talk, but i think this forum is more suitible.--*)

I'm trying to follow this: [http://wiki.squid-cache.org/Features/StoreUrlRewrite](http://wiki.squid-cache.org/Features/StoreUrlRewrite)

Where i am stuck is:[COLOR=DarkRed]
[/COLOR]> 
[COLOR=DarkRed]Then you need a helper. Here's what I've been using: [/COLOR]


```


[COLOR=Black]$| = 1;

while (<>) {
        chomp;
        # print STDERR $_ . "\n";
        if (m/kh(.*?)\.google\.com(.*?)\/(.*?) /) {
                print "http://keyhole-srv.google.com" . $2 . ".SQUIDINTERNAL/" . $3 . "\n";
                # print STDERR "KEYHOLE\n";
        } elsif (m/mt(.*?)\.google\.com(.*?)\/(.*?) /) {
                print "http://map-srv.google.com" . $2 . ".SQUIDINTERNAL/" . $3 . "\n";
                # print STDERR "MAPSRV\n";
        } elsif (m/^http:\/\/([A-Za-z]*?)-(.*?)\.(.*)\.youtube\.com\/get_video\?video_id=(.*) /) {
                # http://lax-v290.lax.youtube.com/get_video?video_id=jqx1ZmzX0k0
                print "http://video-srv.youtube.com.SQUIDINTERNAL/get_video?video_id=" . $4 . "\n";
        } else {
                print $_ . "\n";
        }
}[/COLOR]
```I do not know what to do with this code
Do i compile it? if so, how?
I'm running Debian.

They just say:* configure a rewriter helper* with this script.

---

