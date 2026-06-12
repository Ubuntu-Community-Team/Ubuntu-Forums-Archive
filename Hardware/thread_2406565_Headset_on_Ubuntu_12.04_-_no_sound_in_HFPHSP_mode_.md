---
title: "Headset on Ubuntu 12.04 - no sound in HFP/HSP mode (not the Broadcom issue)"
date: 2018-11-22
forum: Hardware
---

### Post by shaman792 on 2018-11-22
I have an issue getting HSP/HFP mode working on our device. It is  embedded device running Ubuntu 12.04 (upgrade not possible). We are  using Edimax EW-7611ULB (it has Realtek RTL8723BU chip). Bluez version  is 4.101. We are trying to connect Jabra Steel headset.
  
The problem is that in HSP/HFP mode there is no audio. In A2DP mode  it works just fine. It is probably not driver issue as on PC with 18.04  with the same device and drivers it works nicely in A2DP and HSP/HFP.

  There are no errors in Bluetooth or Pulseaudio logs. Everything seems to be working, just the audio is not coming out.

  
I realize it is very old version, but as we are basically locked to it I am getting a bit desperate...

Can anyone help, please?

  
Bluez log here (stripped):
```


bluetoothd[3879]: Bluetooth daemon 4.101
...
bluetoothd[3879]: src/device.c:device_create() Creating device /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: src/device.c:device_set_bonded() bonded 1
bluetoothd[3879]: src/device.c:btd_device_ref() 0xb82abfa8: ref=1
bluetoothd[3879]: src/device.c:device_set_temporary() temporary 0
bluetoothd[3879]: src/device.c:device_probe_drivers() Probing drivers for 50:1A:A5:99:7C:54
bluetoothd[3879]: src/device.c:btd_device_ref() 0xb82abfa8: ref=2
bluetoothd[3879]: input/device.c:input_device_new() Registered interface org.bluez.Input on path /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: src/adapter.c:adapter_get_device() 50:1A:A5:99:7C:54
bluetoothd[3879]: src/device.c:btd_device_ref() 0xb82abfa8: ref=3
bluetoothd[3879]: audio/device.c:audio_device_register() Registered interface org.bluez.Audio on path /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: audio/manager.c:handle_uuid() Found Headset record
bluetoothd[3879]: audio/headset.c:headset_init() Registered interface org.bluez.Headset on path /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: audio/manager.c:handle_uuid() server not enabled for 0000111e-0000-1000-8000-00805f9b34fb (0x111e)
bluetoothd[3879]: audio/manager.c:handle_uuid() Found Audio Sink
bluetoothd[3879]: audio/sink.c:sink_init() Registered interface org.bluez.AudioSink on path /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: audio/manager.c:handle_uuid() Found AV Target
bluetoothd[3879]: audio/control.c:control_init() Registered interface org.bluez.Control on path /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: audio/manager.c:handle_uuid() Found AV Target
bluetoothd[3879]: plugins/mgmtops.c:mgmt_load_link_keys() index 0 keys 1 debug_keys 0
bluetoothd[3879]: plugins/mgmtops.c:mgmtops_load_ltks() index 0 keys 0
bluetoothd[3879]: plugins/mgmtops.c:mgmt_get_conn_list() index 0
bluetoothd[3879]: src/manager.c:btd_manager_register_adapter() Adapter /org/bluez/3879/hci0 registered
bluetoothd[3879]: src/adapter.c:btd_adapter_ref() 0xb82a9b00: ref=5
bluetoothd[3879]: plugins/mgmtops.c:update_settings() new settings d3
bluetoothd[3879]: src/adapter.c:adapter_mode_changed() old 0x00 new 0x02
bluetoothd[3879]: src/adapter.c:set_mode_complete()
bluetoothd[3879]: plugins/mgmtops.c:read_info_complete() mgmtops setting name (null)
bluetoothd[3879]: plugins/mgmtops.c:mgmt_set_dev_class() index 0 major 1 minor 0
bluetoothd[3879]: audio/manager.c:state_changed() /org/bluez/3879/hci0 powered on
bluetoothd[3879]: audio/telephony.c:telephony_init()
bluetoothd[3879]: audio/headset.c:telephony_ready_ind() Telephony plugin initialized
bluetoothd[3879]: audio/headset.c:print_ag_features() HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes"
bluetoothd[3879]: plugins/mgmtops.c:mgmt_disable_cod_cache() index 0
bluetoothd[3879]: Adapter /org/bluez/3879/hci0 has been enabled
bluetoothd[3879]: src/adapter.c:btd_adapter_unref() 0xb82a9b00: ref=4
bluetoothd[3879]: plugins/mgmtops.c:mgmt_event() cond 1
....
bluetoothd[3879]: Endpoint registered: sender=:1.17 path=/MediaEndpoint/HFPAG
bluetoothd[3879]: audio/avdtp.c:avdtp_register_sep() SEP 0xb82ae878 registered: type:0 codec:0 seid:1
bluetoothd[3879]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10003
bluetoothd[3879]: Endpoint registered: sender=:1.17 path=/MediaEndpoint/A2DPSource
bluetoothd[3879]: plugins/mgmtops.c:mgmt_event() Received 24 bytes from management socket
bluetoothd[3879]: plugins/mgmtops.c:mgmt_device_connected() hci0 device 50:1A:A5:99:7C:54 connected eir_len 5
bluetoothd[3879]: src/adapter.c:adapter_get_device() 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/headset.c:headset_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: HEADSET_STATE_DISCONNECTED -> HEADSET_STATE_CONNECTING
bluetoothd[3879]: audio/media.c:headset_state_changed()
bluetoothd[3879]: audio/media.c:media_endpoint_async_call() Calling SetConfiguration: name = :1.17 path = /MediaEndpoint/HFPAG
bluetoothd[3879]: audio/headset.c:headset_connect_cb() /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: Connected to 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/telephony.c:telephony_device_connected() telephony-dummy: device 0xb82ae248 connected
bluetoothd[3879]: audio/headset.c:headset_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: HEADSET_STATE_CONNECTING -> HEADSET_STATE_CONNECTED
bluetoothd[3879]: audio/media.c:headset_state_changed()
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+VGS=15
bluetoothd[3879]: audio/headset.c:headset_set_gain() Ignoring no-change in speaker gain
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+XAPL=0B0E-0972-0123,3
bluetoothd[3879]: audio/headset.c:apple_command() Got Apple command: AT+XAPL=0B0E-0972-0123,3
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+CKPD=200
bluetoothd[3879]: audio/telephony.c:telephony_key_press_req() telephony-dummy: got key press request for 200
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+CPBS="ME"
bluetoothd[3879]: Badly formated or unrecognized command: AT+CPBS="ME"
bluetoothd[3879]: audio/avdtp.c:avdtp_confirm_cb() AVDTP: incoming connect from 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/sink.c:sink_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+CPBR=1
bluetoothd[3879]: Badly formated or unrecognized command: AT+CPBR=1
bluetoothd[3879]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected signaling channel to 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/avdtp.c:avdtp_connect_cb() AVDTP imtu=672, omtu=895
bluetoothd[3879]: audio/avctp.c:avctp_confirm_cb() AVCTP: incoming connect from 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/avctp.c:avctp_set_state() AVCTP Connecting
bluetoothd[3879]: audio/avctp.c:avctp_connect_cb() AVCTP: connected to 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/avctp.c:init_uinput() AVRCP: uinput initialized for 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/avctp.c:avctp_set_state() AVCTP Connected
bluetoothd[3879]: audio/avdtp.c:avdtp_ref() 0xb82afff0: ref=2
bluetoothd[3879]: audio/avdtp.c:session_cb()
bluetoothd[3879]: audio/avdtp.c:avdtp_parse_resp() DISCOVER request succeeded
bluetoothd[3879]: audio/avdtp.c:avdtp_discover_resp() seid 1 type 1 media 0 in use 0
bluetoothd[3879]: audio/avdtp.c:session_cb()
bluetoothd[3879]: audio/avdtp.c:avdtp_parse_resp() GET_CAPABILITIES request succeeded
bluetoothd[3879]: audio/avdtp.c:avdtp_get_capabilities_resp() seid 1 type 1 media 0
bluetoothd[3879]: audio/sink.c:discovery_complete() Discovery complete
bluetoothd[3879]: audio/avdtp.c:avdtp_ref() 0xb82afff0: ref=3
bluetoothd[3879]: audio/a2dp.c:setup_ref() 0xb82b07e8: ref=1
bluetoothd[3879]: audio/media.c:media_endpoint_async_call() Calling SelectConfiguration: name = :1.17 path = /MediaEndpoint/A2DPSource
bluetoothd[3879]: audio/a2dp.c:a2dp_config() a2dp_config: selected SEP 0xb82ae878
bluetoothd[3879]: audio/a2dp.c:setup_ref() 0xb82b07e8: ref=2
bluetoothd[3879]: audio/avdtp.c:avdtp_set_configuration() 0xb82afff0: int_seid=1, acp_seid=1
bluetoothd[3879]: audio/a2dp.c:setup_unref() 0xb82b07e8: ref=1
bluetoothd[3879]: audio/avdtp.c:session_cb()
bluetoothd[3879]: audio/avdtp.c:avdtp_parse_resp() SET_CONFIGURATION request succeeded
bluetoothd[3879]: audio/a2dp.c:setconf_cfm() Source 0xb82ae878: Set_Configuration_Cfm
bluetoothd[3879]: audio/media.c:media_endpoint_async_call() Calling SetConfiguration: name = :1.17 path = /MediaEndpoint/A2DPSource
bluetoothd[3879]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: IDLE -> CONFIGURED
bluetoothd[3879]: audio/avdtp.c:session_cb()
bluetoothd[3879]: audio/avdtp.c:avdtp_parse_resp() OPEN request succeeded
bluetoothd[3879]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected transport channel to 50:1A:A5:99:7C:54
bluetoothd[3879]: audio/avdtp.c:handle_transport_connect() Flushable packets enabled
bluetoothd[3879]: audio/avdtp.c:handle_transport_connect() sk 21, omtu 895, send buffer size 81920
bluetoothd[3879]: audio/a2dp.c:open_cfm() Source 0xb82ae878: Open_Cfm
bluetoothd[3879]: audio/sink.c:stream_setup_complete() Stream successfully created
bluetoothd[3879]: audio/a2dp.c:setup_unref() 0xb82b07e8: ref=0
bluetoothd[3879]: audio/a2dp.c:setup_free() 0xb82b07e8
bluetoothd[3879]: audio/avdtp.c:avdtp_unref() 0xb82afff0: ref=2
bluetoothd[3879]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: CONFIGURED -> OPEN
bluetoothd[3879]: audio/sink.c:sink_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: SINK_STATE_CONNECTING -> SINK_STATE_CONNECTED
bluetoothd[3879]: audio/transport.c:media_transport_acquire() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0: read lock acquired
bluetoothd[3879]: audio/transport.c:media_transport_acquire() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0: write lock acquired
bluetoothd[3879]: audio/transport.c:media_owner_create() Owner created: sender=:1.17 accesstype=rw
bluetoothd[3879]: audio/headset.c:headset_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS
bluetoothd[3879]: audio/media.c:headset_state_changed()
bluetoothd[3879]: audio/transport.c:media_request_create() Request created: method=Acquire id=1
bluetoothd[3879]: audio/transport.c:media_owner_add() Owner :1.17 Request Acquire
bluetoothd[3879]: audio/transport.c:media_transport_add() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0 Owner :1.17
bluetoothd[3879]: audio/headset.c:sco_connect_cb() SCO socket opened for headset /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54
bluetoothd[3879]: audio/headset.c:sco_connect_cb() SCO fd=23
bluetoothd[3879]: /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0: fd(23) ready
bluetoothd[3879]: audio/transport.c:media_owner_remove() Owner :1.17 Request Acquire
bluetoothd[3879]: audio/headset.c:headset_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_PLAYING
bluetoothd[3879]: audio/media.c:headset_state_changed()
bluetoothd[3879]: audio/headset.c:headset_set_gain() Ignoring no-change in speaker gain
bluetoothd[3879]: audio/headset.c:headset_set_gain() Ignoring no-change in microphone gain
bluetoothd[3879]: audio/transport.c:media_request_create() Request created: method=Release id=2
bluetoothd[3879]: audio/transport.c:media_owner_add() Owner :1.17 Request Release
bluetoothd[3879]: Audio connection got disconnected
bluetoothd[3879]: audio/transport.c:media_request_reply() Request Release Reply Success
bluetoothd[3879]: audio/transport.c:media_owner_remove() Owner :1.17 Request Release
bluetoothd[3879]: audio/headset.c:headset_set_state() State changed /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54: HEADSET_STATE_PLAYING -> HEADSET_STATE_CONNECTED
bluetoothd[3879]: audio/media.c:headset_state_changed()
bluetoothd[3879]: audio/transport.c:media_transport_remove() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0 Owner :1.17
bluetoothd[3879]: audio/transport.c:media_transport_release() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0: read lock released
bluetoothd[3879]: audio/transport.c:media_transport_release() Transport /org/bluez/3879/hci0/dev_50_1A_A5_99_7C_54/fd0: write lock released
bluetoothd[3879]: audio/transport.c:media_owner_free() Owner :1.17
bluetoothd[3879]: audio/headset.c:handle_event() Received AT+VGM=15
bluetoothd[3879]: audio/headset.c:headset_set_gain() Ignoring no-change in microphone gain

```

---

### Post by TheFu on 2018-11-22
If you have an extended support contract for 12.04 with Canonical, please contact them.

---

### Post by shaman792 on 2018-11-22
Unfortunately I am not aware of any support contract, therefore I am hoping to get some help from community.

---

