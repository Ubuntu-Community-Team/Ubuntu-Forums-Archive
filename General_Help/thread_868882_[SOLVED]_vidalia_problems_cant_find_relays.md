---
title: "[SOLVED] vidalia problems: cant find relays"
date: 2008-07-24
forum: General Help
---

### Post by harrybazeegar on 2008-07-24
Hi all...
I recently installed tor (apparently without any problem) 
and yesterday I compiled vidalia.

I ran the vidalia control panel from src/vidalia/vidalia and I configured its settings.
I am behind an authenticating HTTP proxy server, so entered the details in the network tab of the settings.

when I clicked start tor, the status on the control panel told me that I am connected to the tor network but it _could not find any relays_... I clicked on view network, and it showed no relays I could reach.

So I got a log of all that happenned yesterday:

```
Jul 21 22:51:42.949 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:51:42.950 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:51:42.950 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:51:42.951 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:51:43.334 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:51:43.334 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:51:43.336 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:52:20.311 [Notice] Renaming old configuration file to "/home/harshath/.vidalia/torrc.orig.1"
Jul 21 22:52:24.190 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:52:24.191 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:52:24.191 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:52:24.192 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:52:25.040 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:52:25.041 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:52:25.042 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:52:25.042 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:52:25.043 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:52:25.044 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:52:25.044 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:52:25.708 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 21 22:52:25.709 [Warning] couldn't find start of hashed material "network-status-version"
Jul 21 22:52:25.710 [Warning] Unable to compute digest of network-status
Jul 21 22:52:25.711 [Warning] Unable to parse networkstatus consensus
Jul 21 22:52:25.712 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 21 22:53:25.417 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:53:25.419 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:53:25.420 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:53:25.421 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:53:25.422 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:53:25.423 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:53:25.943 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:54:35.601 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:54:35.602 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:54:35.604 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:54:35.605 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:54:36.584 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:54:36.586 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:54:36.587 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:54:36.589 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:54:36.591 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:54:36.592 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:54:36.594 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:54:36.595 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 21 22:55:36.828 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:55:36.830 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:55:36.832 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:55:36.834 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:55:36.836 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:55:36.838 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 23:00:41.068 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 23:00:41.071 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 23:00:41.073 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 23:00:41.074 [Notice] No current certificate known for authority ides; launching request.
Jul 21 23:00:41.076 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 23:00:41.078 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 23:00:41.578 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 23:00:41.935 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 21 23:00:41.938 [Warning] couldn't find start of hashed material "network-status-version"
Jul 21 23:00:41.940 [Warning] Unable to compute digest of network-status
Jul 21 23:00:41.942 [Warning] Unable to parse networkstatus consensus
Jul 21 23:00:41.945 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 21 23:31:11.776 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 21 23:55:37.367 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 21 23:57:37.953 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 22 00:07:48.523 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 22 00:07:48.583 [Warning] couldn't find start of hashed material "network-status-version"
Jul 22 00:07:48.586 [Warning] Unable to compute digest of network-status
Jul 22 00:07:48.589 [Warning] Unable to parse networkstatus consensus
Jul 22 00:07:48.591 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 22 00:55:36.400 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 22 01:10:51.433 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching consensus directory.
Jul 22 01:55:36.453 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 22 02:02:42.766 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 22 02:02:42.810 [Warning] couldn't find start of hashed material "network-status-version"
Jul 22 02:02:42.813 [Warning] Unable to compute digest of network-status
Jul 22 02:02:42.816 [Warning] Unable to parse networkstatus consensus
Jul 22 02:02:42.819 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 22 02:33:11.574 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 21 22:51:42.949 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:51:42.950 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:51:42.950 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:51:42.951 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:51:43.334 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:51:43.334 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:51:43.335 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:51:43.336 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:52:20.311 [Notice] Renaming old configuration file to "/home/harshath/.vidalia/torrc.orig.1"
Jul 21 22:52:24.190 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:52:24.191 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:52:24.191 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:52:24.192 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:52:25.040 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:52:25.041 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:52:25.042 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:52:25.042 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:52:25.043 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:52:25.044 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:52:25.044 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:52:25.708 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 21 22:52:25.709 [Warning] couldn't find start of hashed material "network-status-version"
Jul 21 22:52:25.710 [Warning] Unable to compute digest of network-status
Jul 21 22:52:25.711 [Warning] Unable to parse networkstatus consensus
Jul 21 22:52:25.712 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 21 22:53:25.417 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:53:25.419 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:53:25.420 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:53:25.421 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:53:25.422 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:53:25.423 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:53:25.943 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:54:35.601 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 21 22:54:35.602 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 21 22:54:35.604 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 21 22:54:35.605 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 21 22:54:36.584 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 22:54:36.586 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:54:36.587 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:54:36.589 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:54:36.591 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:54:36.592 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:54:36.594 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 22:54:36.595 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 21 22:55:36.828 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 22:55:36.830 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 22:55:36.832 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 22:55:36.834 [Notice] No current certificate known for authority ides; launching request.
Jul 21 22:55:36.836 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 22:55:36.838 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 23:00:41.068 [Notice] No current certificate known for authority moria1; launching request.
Jul 21 23:00:41.071 [Notice] No current certificate known for authority tor26; launching request.
Jul 21 23:00:41.073 [Notice] No current certificate known for authority dizum; launching request.
Jul 21 23:00:41.074 [Notice] No current certificate known for authority ides; launching request.
Jul 21 23:00:41.076 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 21 23:00:41.078 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 21 23:00:41.578 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 21 23:00:41.935 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 21 23:00:41.938 [Warning] couldn't find start of hashed material "network-status-version"
Jul 21 23:00:41.940 [Warning] Unable to compute digest of network-status
Jul 21 23:00:41.942 [Warning] Unable to parse networkstatus consensus
Jul 21 23:00:41.945 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 21 23:31:11.776 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 21 23:55:37.367 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 21 23:57:37.953 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 22 00:07:48.523 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 22 00:07:48.583 [Warning] couldn't find start of hashed material "network-status-version"
Jul 22 00:07:48.586 [Warning] Unable to compute digest of network-status
Jul 22 00:07:48.589 [Warning] Unable to parse networkstatus consensus
Jul 22 00:07:48.591 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 22 00:55:36.400 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching consensus directory.
Jul 22 01:10:51.433 [Warning] Received http status code 302 ("Moved Temporarily") from server '86.59.21.38:80' while fetching consensus directory.
Jul 22 01:55:36.453 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
Jul 22 02:02:42.766 [Warning] Received directory with skewed time (server '213.73.91.31:80'): It seems that our clock is ahead by 2362 days, 13 hours, 49 minutes, or that theirs is behind. Tor requires an accurate clock to work: please check your time and date settings.
Jul 22 02:02:42.810 [Warning] couldn't find start of hashed material "network-status-version"
Jul 22 02:02:42.813 [Warning] Unable to compute digest of network-status
Jul 22 02:02:42.816 [Warning] Unable to parse networkstatus consensus
Jul 22 02:02:42.819 [Warning] Unable to load consensus directory downloaded from server '213.73.91.31:80'. I'll try again soon.
Jul 22 02:33:11.574 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
```

Now is the twist:
today I tried out vidalia again (in some vain hope that it might have righted itself) but now it told me to "Enter your control password(not the hash)".
What does this mean at all?
I clicked cancel to it, so the tor status is stuck at "Authenticating to tor"

so today's log is:
```

Jul 24 20:29:35.101 [Notice] Tor v0.2.0.30 (r15956). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 24 20:29:35.102 [Warning] Linelist option '__HashedControlSessionPassword' has no value. Skipping.
Jul 24 20:29:35.102 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 24 20:29:35.103 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 24 20:29:35.103 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 24 20:29:35.152 [Notice] No current certificate known for authority moria1; launching request.
Jul 24 20:29:35.153 [Notice] No current certificate known for authority tor26; launching request.
Jul 24 20:29:35.153 [Notice] No current certificate known for authority dizum; launching request.
Jul 24 20:29:35.153 [Notice] No current certificate known for authority ides; launching request.
Jul 24 20:29:35.154 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 24 20:29:35.155 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 24 20:29:35.155 [Notice] I learned some more directory information, but not enough to build a circuit: We have no network-status consensus.
Jul 24 20:29:35.156 [Notice] No current certificate known for authority moria1; launching request.
Jul 24 20:29:35.156 [Notice] No current certificate known for authority tor26; launching request.
Jul 24 20:29:35.157 [Notice] No current certificate known for authority dizum; launching request.
Jul 24 20:29:35.158 [Notice] No current certificate known for authority ides; launching request.
Jul 24 20:29:35.158 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 24 20:29:35.159 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 24 20:29:35.553 [Warning] Received http status code 302 ("Moved Temporarily") from server '194.109.206.212:80' while fetching "/tor/keys/fp/E2A2AF570166665D738736D0DD58169CC61D8A8B+14C131DFC5C6F93646BE72FA1401C02A8DF2E8B4+E8A9C45EDE6D711294FADF8E7951F4DE6CA56B58+27B6B5996C426270A5C95488AA5BCEB6BCC86956+81349FC1F2DBA2C2C11B45CB9706637D480AB913+585769C78764D58426B8B52B6651A5A71137189A".
Jul 24 20:29:35.554 [Notice] No current certificate known for authority moria1; launching request.
Jul 24 20:29:35.555 [Notice] No current certificate known for authority tor26; launching request.
Jul 24 20:29:35.556 [Notice] No current certificate known for authority dizum; launching request.
Jul 24 20:29:35.557 [Notice] No current certificate known for authority ides; launching request.
Jul 24 20:29:35.558 [Notice] No current certificate known for authority gabelmoo; launching request.
Jul 24 20:29:35.559 [Notice] No current certificate known for authority dannenberg; launching request.
Jul 24 20:29:37.425 [Warning] Received http status code 302 ("Moved Temporarily") from server '88.198.7.215:80' while fetching consensus directory.
```

so what is the problem with this? why wont it connect to the tor network?

PS: my friends on windows are able to connect to the tor network without probs... thats partly what is pissing me off :(

---

### Post by pauper on 2008-07-24
Did you follow any of these guides?

[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)
[http://www.privoxy.org/user-manual](http://www.privoxy.org/user-manual)
[http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html](http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html)

> ...it told me to "Enter your control password(not the hash)".

[http://trac.vidalia-project.net/wiki/FAQ#ExistingTor](http://trac.vidalia-project.net/wiki/FAQ#ExistingTor)

---

### Post by harrybazeegar on 2008-07-26
Okay, I figured it out.

thanks :)

---

### Post by foxmajik on 2008-07-26
> **harrybazeegar said:**
> Okay, I figured it out.

thanks :)

Great, so how about telling us how you resolved the problem?

---

### Post by rainspeaker on 2010-01-25
I am not a terribly experience ubuntu user, but I do know that Vidalia uses a 'control password' to communicate securely with Tor. This control password is generated when Vidalia tells Tor to start up. If you closed Vidalia without shutting down Tor properly, or something like that, Vidalia probably doesn't know the password anymore and you'll have to force Tor to shut down. I managed this by typing 

> sudo killall tor

so as long as you have sudo privileges, this will hopefully work. If not, I apologize. Best of luck!

---

