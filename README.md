# LIFX Specification
LIFX LAN protocol specifications generated from the decompiled LIFX Android application.

__*__ = [officially documented](https://lan.developer.lifx.com/docs)

**Payload format:**
```
name [size in bytes] type
  value = enum|bool
  ...
...
```

## Structs
#### HSBK *
```
hue        [2] uint
saturation [2] uint
brightness [2] uint
kelvin     [2] uint
```

#### RGBW
```
red   [2] uint
green [2] uint
blue  [2] uint
white [2] uint
```

#### Xyz
```
x [4] float
y [4] float
z [4] float
```

## Messages
#### 1 (DEVICE_SET_SITE)
```
site [6] byte[]
```

#### 2 (DEVICE_GET_SERVICE) *
*empty*

#### 3 (DEVICE_STATE_SERVICE) *
```
service [1] int
  0x1 = UDP
  0x2 = TCP
  0x3 = ONBOARDING
  0x4 = OTA
port    [4] uint
```

#### 4 (DEVICE_GET_TIME)
*empty*

#### 5 (DEVICE_SET_TIME)
```
time [8] int
```

#### 6 (DEVICE_STATE_TIME)
```
time [8] int
```

#### 7 (DEVICE_GET_RESET_SWITCH)
*empty*

#### 8 (DEVICE_STATE_RESET_SWITCH)
```
position [1] uint
```

#### 9 (DEVICE_GET_DUMMY_LOAD)
*empty*

#### 10 (DEVICE_SET_DUMMY_LOAD)
```
on [1] bool
  0x0 = false
  0x1 = true
```

#### 11 (DEVICE_STATE_DUMMY_LOAD)
```
on [1] bool
  0x0 = false
 !0x0 = true
```

#### 12 (DEVICE_GET_HOST_INFO) *
*empty*

#### 13 (DEVICE_STATE_HOST_INFO) *
```
signal         [4] float
tx             [4] uint
rx             [4] uint
mcuTemperature [2] uint
```

#### 14 (DEVICE_GET_HOST_FIRMWARE) *
*empty*

#### 15 (DEVICE_STATE_HOST_FIRMWARE) *
```
build   [8] int
install [8] int
version [4] uint
```

#### 16 (DEVICE_GET_WIFI_INFO) *
*empty*

#### 17 (DEVICE_STATE_WIFI_INFO) *
```
signal         [4] float
tx             [4] uint
rx             [4] uint
mcuTemperature [2] int
```

#### 18 (DEVICE_GET_WIFI_FIRMWARE) *
*empty*

#### 19 (DEVICE_STATE_WIFI_FIRMWARE) *
```
build   [8] int
install [8] int
version [4] uint
```

#### 20 (DEVICE_GET_POWER) *
*empty*

#### 21 (DEVICE_SET_POWER) *
```
level [2] uint
```

#### 22 (DEVICE_STATE_POWER) *
```
level [2] uint
```
#### 23 (DEVICE_GET_LABEL) *
*empty*

#### 24 (DEVICE_SET_LABEL) *
```
label [32] string
```

#### 25 (DEVICE_STATE_LABEL) *
```
label [32] string
```

#### 26 (DEVICE_GET_TAGS)
*empty*

#### 27 (DEVICE_SET_TAGS)
```
tags [8] int
```

#### 28 (DEVICE_STATE_TAGS)
```
tags [8] int
```

#### 29 (DEVICE_GET_TAG_LABELS)
```
tags [8] int
```

#### 30 (DEVICE_SET_TAG_LABELS)
```
tags  [8]  int
label [32] string
```

#### 31 (DEVICE_STATE_TAG_LABELS)
```
tags  [8]  int
label [32] string
```

#### 32 (DEVICE_GET_VERSION) *
*empty*

#### 33 (DEVICE_STATE_VERSION) *
```
vendor  [4] uint
product [4] uint
version [4] uint
```

#### 34 (DEVICE_GET_INFO) *
*empty*

#### 35 (DEVICE_STATE_INFO) *
```
time     [8] int
uptime   [8] int
downtime [8] int
```

#### 36 (DEVICE_GET_MCU_RAIL_VOLTAGE)
*empty*

#### 37 (DEVICE_STATE_MCU_RAIL_VOLTAGE)
```
voltage [4] uint
```

#### 38 (DEVICE_SET_REBOOT)
*empty*

#### 39 (DEVICE_SET_FACTORY_TEST_MODE)
```
on [1] bool
  0x0 = false
 !0x0 = true
```

#### 40 (DEVICE_DISABLE_FACTORY_TEST_MODE)
*empty*

#### 41 (DEVICE_STATE_FACTORY_TEST_MODE)
```
on       [1] bool
  0x0 = false
 !0x0 = true
disabled [1] bool
  0x0 = false
 !0x0 = true
```

#### 42 (DEVICE_STATE_SITE)
```
site [6] byte[]
```

#### 43 (DEVICE_STATE_REBOOT)
*empty*

#### 44 (DEVICE_SET_PAN_GATEWAY)
```
enabled [1] bool
  0x0 = false
 !0x0 = true
```

#### 45 (DEVICE_ACKNOWLEDGEMENT) *
*empty*

#### 46 (DEVICE_SET_FACTORY_RESET)
*empty*

#### 47 (DEVICE_STATE_FACTORY_RESET)
*empty*

#### 48 (DEVICE_GET_LOCATION) *
*empty*

#### 49 (DEVICE_SET_LOCATION)
```
location  [16] byte[]
label     [32] string
updatedAt [8]  int
```

#### 50 (DEVICE_STATE_LOCATION) *
```
location  [16] byte[]
label     [32] string
updatedAt [8]  int
```

#### 51 (DEVICE_GET_GROUP) *
*empty*

#### 52 (DEVICE_SET_GROUP)
```
group     [16] byte[]
label     [32] string
updatedAt [8]  int
```

#### 53 (DEVICE_STATE_GROUP) *
```
group     [16] byte[]
label     [32] string
updatedAt [8] int
```

#### 54 (DEVICE_GET_OWNER)
*empty*

#### 55 (DEVICE_SET_OWNER)
```
owner     [16] byte[]
label     [32] string
updatedAt [8]  int
```

#### 56 (DEVICE_STATE_OWNER)
```
owner     [16] byte[]
label     [32] string
updatedAt [8]  int
```

#### 57 (DEVICE_GET_FACTORY_TEST_MODE)
*empty*

#### 58 (DEVICE_ECHO_REQUEST) *
```
payload [64] byte[]
```

#### 59 (DEVICE_ECHO_RESPONSE) *
```
payload [64] byte[]
```

#### 101 (LIGHT_GET) *
*empty*

#### 102 (LIGHT_SET_COLOR) *
```
stream   [2] uint
color    [8] HSBK
duration [4] uint
```

#### 103 (LIGHT_SET_WAVEFORM)
```
stream       [2] uint
is_transient [1] bool
  0x0 = false
 !0x0 = true
color        [8] HSBK
period       [4] uint
cycles       [4] float
skewRatio    [2] int
waveform     [1] int
  0x0 = SAW
  0x1 = SINE
  0x2 = HALF_SINE
  0x3 = TRIANGLE
  0x4 = PULSE
```

#### 104 (LIGHT_SET_DIM_ABSOLUTE)
```
brightness [2] int
duration   [4] uint
```

#### 105 (LIGHT_SET_DIM_RELATIVE)
```
brightness [4] int
duration   [4] uint
```

#### 106 (LIGHT_SET_RGBW)
```
color [8] RGBW
```

#### 107 (LIGHT_STATE) *
```
color [8]  HSBK
dim   [2]  int
power [2]  uint
label [32] string
tags  [8]  int
```

#### 108 (LIGHT_GET_RAIL_VOLTAGE)
*empty*

#### 109 (LIGHT_STATE_RAIL_VOLTAGE)
```
voltage [4] uint
```

#### 110 (LIGHT_GET_TEMPERATURE)
*empty*

#### 111 (LIGHT_STATE_TEMPERATURE)
```
temperature [2] int
```

#### 112 (LIGHT_SET_CALIBRATION_COEFFICIENTS)
```
r [12] Xyz
g [12] Xyz
b [12] Xyz
w [12] Xyz
```

#### 113 (LIGHT_SET_SIMPLE_EVENT)
```
index    [1] uint
time     [8] int
power    [2] uint
duration [4] uint
waveform [1] int
  0x0 = SAW
  0x1 = SINE
  0x2 = HALF_SINE
  0x3 = TRIANGLE
  0x4 = PULSE
```

#### 114 (LIGHT_GET_SIMPLE_EVENT)
```
index [1] uint
```

#### 115 (LIGHT_STATE_SIMPLE_EVENT)
```
index    [1] uint
time     [8] int
power    [2] uint
duration [4] uint
waveform [1] int
  0x0 = SAW
  0x1 = SINE
  0x2 = HALF_SINE
  0x3 = TRIANGLE
  0x4 = PULSE
max      [2] uint
```

#### 116 (LIGHT_GET_POWER) *
*empty*

#### 117 (LIGHT_SET_POWER) *
```
level    [2] uint
duration [4] uint
```

#### 118 (LIGHT_STATE_POWER) *
```
lavel [2] uint
```

#### 119 (LIGHT_SET_WAVEFORM_OPTIONAL)
```
stream         [2] uint
is_transient   [1] bool
  0x0 = false
 !0x0 = true
color          [8] HSBK
period         [4] uint
cycles         [4] float
skewRatio      [2] int
waveform       [1] int
  0x0 = SAW
  0x1 = SINE
  0x2 = HALF_SINE
  0x3 = TRIANGLE
  0x4 = PULSE
set_hue        [1] bool
  0x0 = false
 !0x0 = true
set_saturation [1] bool
  0x0 = false
 !0x0 = true
set_brightness [1] bool
  0x0 = false
 !0x0 = true
set_kelvin     [1] bool
  0x0 = false
 !0x0 = true
```

#### 201 (WAN_GET)
*empty*

#### 202 (WAN_SET)
```
active [1] bool
  0x0 = false
 !0x0 = true
```

#### 203 (WAN_STATE)
```
status [1] int
  0x0 = OFF
  0x1 = CONNECTED
  0x2 = ERROR_UNAUTHORIZED
  0x3 = ERROR_OVER_CAPACITY
  0x4 = ERROR_OVER_RATE
  0x5 = ERROR_NO_ROUTE
  0x6 = ERROR_INTERNAL_CLIENT
  0x7 = ERROR_INTERNAL_SERVER
  0x8 = ERROR_DNS_FAILURE
  0x9 = ERROR_SSL_FAILURE
  0xa = ERROR_CONNECTION_REFUSED
  0xb = CONNECTING
```

#### 204 (WAN_GET_AUTH_KEY)
*empty*

#### 205 (WAN_SET_AUTH_KEY)
```
key [32] byte[]
```

#### 206 (WAN_STATE_AUTH_KEY)
```
key [32] byte[]
```

#### 207 (WAN_SET_KEEP_ALIVE)
```
seconds [2] uint
```

#### 208 (WAN_STATE_KEEP_ALIVE)
*empty*

#### 209 (WAN_SET_HOST)
```
host                 [32] string
insecure_skip_verify [1]  bool
  0x0 = false
 !0x1 = true
```

#### 210 (WAN_GET_HOST)
*empty*

#### 211 (WAN_STATE_HOST)
```
host                 [32] string
insecure_skip_verify [1]  bool
  0x0 = false
 !0x1 = true
```

#### 301 (WIFI_GET)
```
interface [1] int
  0x1 = SOFT_AP
  0x2 = STATION
```

#### 302 (WIFI_SET)
```
network_interface [1] int
  0x1 = SOFT_AP
  0x2 = STATION
active            [1] bool
  0x0 = false
 !0x0 = true
```

#### 303 (WIFI_STATE)
```
network_interface [1] int
  0x1 = SOFT_AP
  0x2 = STATION
status            [1] int
  0x0 = CONNECTING
  0x1 = CONNECTED
  0x2 = FAILED
  0x3 = OFF
```

#### 304 (WIFI_GET_ACCESS_POINTS)
*empty*

#### 305 (WIFI_SET_ACCESS_POINT)
```
network_interface [1]  int
  0x1 = SOFT_AP
  0x2 = STATION
ssid              [32] string
pass              [64] string
security          [1]  int
  0x0 = UNKNOWN
  0x1 = OPEN
  0x2 = WEP_PSK
  0x3 = WPA_TKIP_PSK
  0x4 = WPA_AES_PSK
  0x5 = WPA2_AES_PSK
  0x6 = WPA2_TKIP_PSK
  0x7 = WPA2_MIXED_PSK
```

#### 306 (WIFI_STATE_ACCESS_POINTS)
```
network_interface [1]  int
  0x1 = SOFT_AP
  0x2 = STATION
ssid              [32] string
security          [1]  int
  0x0 = UNKNOWN
  0x1 = OPEN
  0x2 = WEP_PSK
  0x3 = WPA_TKIP_PSK
  0x4 = WPA_AES_PSK
  0x5 = WPA2_AES_PSK
  0x6 = WPA2_TKIP_PSK
  0x7 = WPA2_MIXED_PSK
strength [2] int
channel  [2] uint
```

#### 307 (WIFI_GET_ACCESS_POINT)
```
network_interface [1]  int
  0x1 = SOFT_AP
  0x2 = STATION
```

#### 308 (WIFI_STATE_ACCESS_POINT)
```
network_interface [1]  int
  0x1 = SOFT_AP
  0x2 = STATION
ssid              [32] string
pass              [32] string
security          [1]  int
  0x0 = UNKNOWN
  0x1 = OPEN
  0x2 = WEP_PSK
  0x3 = WPA_TKIP_PSK
  0x4 = WPA_AES_PSK
  0x5 = WPA2_AES_PSK
  0x6 = WPA2_TKIP_PSK
  0x7 = WPA2_MIXED_PSK     
```

#### 309 (WIFI_SET_ACCESS_POINT_BROADCAST)
```
network_interface [1]  int
  0x1 = SOFT_AP
  0x2 = STATION
ssid              [32] string
pass              [64] string
security          [1]  int
  0x0 = UNKNOWN
  0x1 = OPEN
  0x2 = WEP_PSK
  0x3 = WPA_TKIP_PSK
  0x4 = WPA_AES_PSK
  0x5 = WPA2_AES_PSK
  0x6 = WPA2_TKIP_PSK
  0x7 = WPA2_MIXED_PSK
key               [16] byte[]
```

#### 401 (SENSOR_GET_AMBIENT_LIGHT)
*empty*

#### 402 (SENSOR_STATE_AMBIENT_LIGHT)
```
lux [4] float
```

#### 403 (SENSOR_GET_DIMMER_VOLTAGE)
*empty*

#### 404 (SENSOR_STATE_DIMMER_VOLTAGE)
```
voltage [4] uint
```
