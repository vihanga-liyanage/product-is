# IAM Performance Test Results

During each release, we execute various automated performance test scenarios and publish the results.

| Test Scenarios | Description |
| --- | --- |
| Authenticate Super Tenant User | Select random super tenant users and authenticate through the RemoteUserStoreManagerService. |
| SAML2 SSO Redirect Binding | Obtain a SAML 2 assertion response using redirect binding. |
| Auth Code Grant Redirect With Consent | Obtain an access token using the OAuth 2.0 authorization code grant type. |
| Implicit Grant Redirect With Consent | Obtain an access token using the OAuth 2.0 implicit grant type. |
| Password Grant Type | Obtain an access token using the OAuth 2.0 password grant type. |
| Client Credentials Grant Type | Obtain an access token using the OAuth 2.0 client credential grant type. |
| OIDC Auth Code Grant Redirect With Consent | Obtain an access token and an id token using the OAuth 2.0 authorization code grant type. |
| OIDC Implicit Grant Redirect With Consent | Obtain an access token and an id token using the OAuth 2.0 implicit grant type. |
| OIDC Password Grant Type | Obtain an access token and an id token using the OAuth 2.0 password grant type. |
| OIDC Auth Code Request Path Authenticator With Consent | Obtain an access token and an id token using the request path authenticator. |

Our test client is [Apache JMeter](https://jmeter.apache.org/index.html). We test each scenario for a fixed duration of
time and split the test results into warm-up and measurement parts and use the measurement part to compute the
performance metrics. For this particular instance, the duration of each test is **15 minutes** and the warm-up period is **5 minutes**.

We run the performance tests under different numbers of concurrent users and heap sizes to gain a better understanding on how the server reacts to different loads.

The main performance metrics:

1. **Throughput**: The number of requests that the WSO2 Identity Server processes during a specific time interval (e.g. per second).
2. **Response Time**: The end-to-end latency for a given operation of the WSO2 Identity Server. The complete distribution of response times was recorded.

In addition to the above metrics, we measure the load average and several memory-related metrics.

The following are the test parameters.

| Test Parameter | Description | Values |
| --- | --- | --- |
| Scenario Name | The name of the test scenario. | Refer to the above table. |
| Heap Size | The amount of memory allocated to the application | 2G |
| Concurrent Users | The number of users accessing the application at the same time. | 50, 100, 150, 300, 500 |
| IS Instance Type | The AWS instance type used to run the Identity Server. | [**c5.large**](https://aws.amazon.com/ec2/instance-types/) |

The following are the measurements collected from each performance test conducted for a given combination of
test parameters.

| Measurement | Description |
| --- | --- |
| Error % | Percentage of requests with errors |
| Average Response Time (ms) | The average response time of a set of results |
| Standard Deviation of Response Time (ms) | The Standard Deviation of the response time. |
| 99th Percentile of Response Time (ms) | 99% of the requests took no more than this time. The remaining samples took at least as long as this |
| Throughput (Requests/sec) | The throughput measured in requests per second. |
| Average Memory Footprint After Full GC (M) | The average memory consumed by the application after a full garbage collection event. |

The following is the summary of performance test results collected for the measurement period.

|  Scenario Name | Concurrent Users | Label | Error % | Throughput (Requests/sec) | Average Response Time (ms) | Standard Deviation of Response Time (ms) | 99th Percentile of Response Time (ms) | WSO2 Identity Server GC Throughput (%) |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
|  Authenticate Super Tenant User | 50 | Authenticate | 0 | 945.7 | 52.69 | 24.72 | 133 | 98.97 |
|  Authenticate Super Tenant User | 100 | Authenticate | 0 | 834.48 | 119.64 | 48.31 | 267 | 98.77 |
|  Authenticate Super Tenant User | 150 | Authenticate | 0 | 832.41 | 180.03 | 74.4 | 397 | 98.69 |
|  Authenticate Super Tenant User | 300 | Authenticate | 0 | 775.11 | 387.02 | 166.77 | 855 | 98.37 |
|  Authenticate Super Tenant User | 500 | Authenticate | 0 | 771.22 | 648.07 | 274.38 | 1399 | 97.65 |
|  Auth Code Grant Redirect With Consent | 50 | Common Auth Login HTTP Request | 0 | 20.46 | 247.74 | 170.22 | 691 | 99.21 |
|  Auth Code Grant Redirect With Consent | 50 | Common Auth Login HTTP Request Redirect | 0 | 20.45 | 303.78 | 237.07 | 1031 | 99.21 |
|  Auth Code Grant Redirect With Consent | 50 | Get Authorization Code | 0 | 20.45 | 352.61 | 250.34 | 995 | 99.21 |
|  Auth Code Grant Redirect With Consent | 50 | Get access token | 0 | 20.46 | 1192.43 | 802.42 | 2735 | 99.21 |
|  Auth Code Grant Redirect With Consent | 50 | Send request to authorize end poiont | 0 | 20.48 | 347.43 | 254.06 | 1039 | 99.21 |
|  Auth Code Grant Redirect With Consent | 100 | Common Auth Login HTTP Request | 0 | 20.42 | 494.45 | 371.57 | 1607 | 99.19 |
|  Auth Code Grant Redirect With Consent | 100 | Common Auth Login HTTP Request Redirect | 0 | 20.43 | 641.79 | 521.23 | 2303 | 99.19 |
|  Auth Code Grant Redirect With Consent | 100 | Get Authorization Code | 0 | 20.4 | 708.93 | 538.76 | 2207 | 99.19 |
|  Auth Code Grant Redirect With Consent | 100 | Get access token | 0 | 20.37 | 2317.21 | 1597.87 | 5599 | 99.19 |
|  Auth Code Grant Redirect With Consent | 100 | Send request to authorize end poiont | 0 | 20.41 | 729.36 | 560.29 | 2303 | 99.19 |
|  Auth Code Grant Redirect With Consent | 150 | Common Auth Login HTTP Request | 0 | 20 | 774.22 | 594.03 | 2575 | 99.11 |
|  Auth Code Grant Redirect With Consent | 150 | Common Auth Login HTTP Request Redirect | 0 | 19.99 | 999.28 | 798.02 | 3439 | 99.11 |
|  Auth Code Grant Redirect With Consent | 150 | Get Authorization Code | 0 | 19.95 | 1130.13 | 865.76 | 3455 | 99.11 |
|  Auth Code Grant Redirect With Consent | 150 | Get access token | 0 | 19.92 | 3432.9 | 2317.33 | 8383 | 99.11 |
|  Auth Code Grant Redirect With Consent | 150 | Send request to authorize end poiont | 0 | 19.97 | 1146.96 | 877.39 | 3503 | 99.11 |
|  Auth Code Grant Redirect With Consent | 300 | Common Auth Login HTTP Request | 0 | 19.83 | 1582.62 | 1220.87 | 5087 | 98.99 |
|  Auth Code Grant Redirect With Consent | 300 | Common Auth Login HTTP Request Redirect | 0 | 19.8 | 2053.78 | 1564.05 | 6591 | 98.99 |
|  Auth Code Grant Redirect With Consent | 300 | Get Authorization Code | 0 | 19.76 | 2362.82 | 1720.73 | 6495 | 98.99 |
|  Auth Code Grant Redirect With Consent | 300 | Get access token | 0 | 19.69 | 6604.02 | 4289.81 | 15103 | 98.99 |
|  Auth Code Grant Redirect With Consent | 300 | Send request to authorize end poiont | 0 | 19.76 | 2519.93 | 1935.13 | 7647 | 98.99 |
|  Auth Code Grant Redirect With Consent | 500 | Common Auth Login HTTP Request | 0 | 20.35 | 2110 | 1417.38 | 5663 | 98.92 |
|  Auth Code Grant Redirect With Consent | 500 | Common Auth Login HTTP Request Redirect | 0 | 20.32 | 2912.78 | 2073.11 | 7551 | 98.92 |
|  Auth Code Grant Redirect With Consent | 500 | Get Authorization Code | 0 | 20.41 | 3589.13 | 2461.04 | 8447 | 98.92 |
|  Auth Code Grant Redirect With Consent | 500 | Get access token | 0 | 20.52 | 11989.6 | 7644.79 | 23551 | 98.92 |
|  Auth Code Grant Redirect With Consent | 500 | Send request to authorize end poiont | 0 | 20.37 | 3600.61 | 2508.13 | 8831 | 98.92 |
|  Client Credentials Grant Type | 50 | Get Token Client Credential Grant | 0 | 1681.78 | 29.58 | 25.63 | 73 | 99.09 |
|  Client Credentials Grant Type | 100 | Get Token Client Credential Grant | 0 | 1748.82 | 57.02 | 35.44 | 171 | 99.04 |
|  Client Credentials Grant Type | 150 | Get Token Client Credential Grant | 0 | 1608.24 | 93.11 | 66.44 | 299 | 98.85 |
|  Client Credentials Grant Type | 300 | Get Token Client Credential Grant | 0 | 1435.69 | 208.85 | 1143.52 | 647 | 98.56 |
|  Client Credentials Grant Type | 500 | Get Token Client Credential Grant | 0.03 | 1366.72 | 365.69 | 1513.47 | 999 | 97.93 |
|  Implicit Grant Redirect With Consent | 50 | Common Auth Login HTTP Request | 0 | 38.94 | 299.49 | 196 | 751 | 99.1 |
|  Implicit Grant Redirect With Consent | 50 | Common Auth Login HTTP Request Redirect | 0 | 38.95 | 319.95 | 234.95 | 935 | 99.1 |
|  Implicit Grant Redirect With Consent | 50 | Get Access token | 0 | 38.94 | 270.12 | 196.23 | 799 | 99.1 |
|  Implicit Grant Redirect With Consent | 50 | Send request to authorize end point | 0 | 38.94 | 394.24 | 279.29 | 1039 | 99.1 |
|  Implicit Grant Redirect With Consent | 100 | Common Auth Login HTTP Request | 0 | 38.95 | 566.1 | 374.51 | 1575 | 99.08 |
|  Implicit Grant Redirect With Consent | 100 | Common Auth Login HTTP Request Redirect | 0 | 38.95 | 665.63 | 510.92 | 2111 | 99.08 |
|  Implicit Grant Redirect With Consent | 100 | Get Access token | 0 | 38.93 | 531.74 | 412.73 | 1815 | 99.08 |
|  Implicit Grant Redirect With Consent | 100 | Send request to authorize end point | 0 | 38.97 | 802.24 | 593.61 | 2319 | 99.08 |
|  Implicit Grant Redirect With Consent | 150 | Common Auth Login HTTP Request | 0 | 39.48 | 822.2 | 558.77 | 2463 | 98.96 |
|  Implicit Grant Redirect With Consent | 150 | Common Auth Login HTTP Request Redirect | 0 | 39.49 | 1012.85 | 778.94 | 3199 | 98.96 |
|  Implicit Grant Redirect With Consent | 150 | Get Access token | 0 | 39.5 | 750.05 | 580.49 | 2543 | 98.96 |
|  Implicit Grant Redirect With Consent | 150 | Send request to authorize end point | 0 | 39.47 | 1205.47 | 895.42 | 3439 | 98.96 |
|  Implicit Grant Redirect With Consent | 300 | Common Auth Login HTTP Request | 0 | 40.55 | 1537.09 | 1005.45 | 4383 | 98.75 |
|  Implicit Grant Redirect With Consent | 300 | Common Auth Login HTTP Request Redirect | 0 | 40.54 | 1967.18 | 1501.04 | 5983 | 98.75 |
|  Implicit Grant Redirect With Consent | 300 | Get Access token | 0 | 40.58 | 1335.38 | 961.71 | 4031 | 98.75 |
|  Implicit Grant Redirect With Consent | 300 | Send request to authorize end point | 0 | 40.51 | 2526.7 | 1918.76 | 7295 | 98.75 |
|  Implicit Grant Redirect With Consent | 500 | Common Auth Login HTTP Request | 0 | 40.9 | 2387.96 | 1461.93 | 6111 | 98.65 |
|  Implicit Grant Redirect With Consent | 500 | Common Auth Login HTTP Request Redirect | 0 | 40.93 | 3298.4 | 2439.9 | 9215 | 98.65 |
|  Implicit Grant Redirect With Consent | 500 | Get Access token | 0 | 41.12 | 2302.06 | 1540.9 | 6015 | 98.65 |
|  Implicit Grant Redirect With Consent | 500 | Send request to authorize end point | 0 | 41.05 | 4127.86 | 3147.08 | 11839 | 98.65 |
|  Password Grant Type | 50 | GetToken_Password_Grant | 0 | 145.86 | 342.51 | 241.79 | 975 | 99.4 |
|  Password Grant Type | 100 | GetToken_Password_Grant | 0 | 142.78 | 699.65 | 540.98 | 2415 | 99.26 |
|  Password Grant Type | 150 | GetToken_Password_Grant | 0 | 145.31 | 1029.98 | 791.02 | 3519 | 99.22 |
|  Password Grant Type | 300 | GetToken_Password_Grant | 0 | 144.13 | 2080.51 | 1512.61 | 6399 | 99.07 |
|  Password Grant Type | 500 | GetToken_Password_Grant | 0 | 149.17 | 3337.76 | 2255.82 | 8703 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 50 | Common Auth Login HTTP Request | 0 | 20.09 | 252.98 | 170.12 | 715 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 50 | Common Auth Login HTTP Request Redirect | 0 | 20.1 | 304.5 | 235.77 | 1019 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 50 | Get Authorization Code | 0 | 20.09 | 355.4 | 250.77 | 983 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 50 | Get tokens | 0 | 20.08 | 1221.53 | 815.37 | 2799 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 50 | Send request to authorize end poiont | 0 | 20.1 | 352.18 | 259.97 | 1063 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 100 | Common Auth Login HTTP Request | 0 | 20.13 | 505.97 | 365.53 | 1583 | 99.2 |
|  OIDC Auth Code Grant Redirect With Consent | 100 | Common Auth Login HTTP Request Redirect | 0 | 20.13 | 653.56 | 531.77 | 2351 | 99.2 |
|  OIDC Auth Code Grant Redirect With Consent | 100 | Get Authorization Code | 0 | 20.12 | 716.48 | 540.21 | 2223 | 99.2 |
|  OIDC Auth Code Grant Redirect With Consent | 100 | Get tokens | 0 | 20.13 | 2349.19 | 1608.99 | 5663 | 99.2 |
|  OIDC Auth Code Grant Redirect With Consent | 100 | Send request to authorize end poiont | 0 | 20.13 | 729.94 | 556.91 | 2351 | 99.2 |
|  OIDC Auth Code Grant Redirect With Consent | 150 | Common Auth Login HTTP Request | 0 | 20.3 | 773.31 | 552.3 | 2447 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 150 | Common Auth Login HTTP Request Redirect | 0 | 20.28 | 987.76 | 810.57 | 3439 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 150 | Get Authorization Code | 0 | 20.29 | 1101.04 | 836.29 | 3391 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 150 | Get tokens | 0 | 20.23 | 3362.01 | 2247.76 | 8031 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 150 | Send request to authorize end poiont | 0 | 20.25 | 1155.09 | 901 | 3631 | 99.08 |
|  OIDC Auth Code Grant Redirect With Consent | 300 | Common Auth Login HTTP Request | 0 | 19.74 | 1607.94 | 1225.99 | 5279 | 99.04 |
|  OIDC Auth Code Grant Redirect With Consent | 300 | Common Auth Login HTTP Request Redirect | 0 | 19.74 | 2077.82 | 1587.53 | 6623 | 99.04 |
|  OIDC Auth Code Grant Redirect With Consent | 300 | Get Authorization Code | 0 | 19.73 | 2357.09 | 1706.64 | 6719 | 99.04 |
|  OIDC Auth Code Grant Redirect With Consent | 300 | Get tokens | 0 | 19.65 | 6566.97 | 4274.6 | 14975 | 99.04 |
|  OIDC Auth Code Grant Redirect With Consent | 300 | Send request to authorize end poiont | 0 | 19.59 | 2531.09 | 1941.49 | 7711 | 99.04 |
|  OIDC Auth Code Grant Redirect With Consent | 500 | Common Auth Login HTTP Request | 0 | 20.03 | 2168.07 | 1447.64 | 5759 | 98.84 |
|  OIDC Auth Code Grant Redirect With Consent | 500 | Common Auth Login HTTP Request Redirect | 0 | 20.03 | 3103.22 | 2090.82 | 7743 | 98.84 |
|  OIDC Auth Code Grant Redirect With Consent | 500 | Get Authorization Code | 0 | 20.02 | 3790.32 | 2504.57 | 8703 | 98.84 |
|  OIDC Auth Code Grant Redirect With Consent | 500 | Get tokens | 0 | 19.97 | 11909.87 | 7518 | 23039 | 98.84 |
|  OIDC Auth Code Grant Redirect With Consent | 500 | Send request to authorize end poiont | 0 | 19.99 | 3683.26 | 2492 | 9151 | 98.84 |
|  OIDC Implicit Grant Redirect With Consent | 50 | Common Auth Login HTTP Request | 0 | 26.43 | 276.68 | 185.59 | 759 | 99.22 |
|  OIDC Implicit Grant Redirect With Consent | 50 | Common Auth Login HTTP Request Redirect | 0 | 26.43 | 335.18 | 254.58 | 1087 | 99.22 |
|  OIDC Implicit Grant Redirect With Consent | 50 | Get tokens | 0 | 26.42 | 890.4 | 596.93 | 2175 | 99.22 |
|  OIDC Implicit Grant Redirect With Consent | 50 | Send request to authorize end point | 0 | 26.43 | 388.1 | 277.86 | 1119 | 99.22 |
|  OIDC Implicit Grant Redirect With Consent | 100 | Common Auth Login HTTP Request | 0 | 25.98 | 555.17 | 403.62 | 1727 | 99.07 |
|  OIDC Implicit Grant Redirect With Consent | 100 | Common Auth Login HTTP Request Redirect | 0 | 25.99 | 718.68 | 574.36 | 2575 | 99.07 |
|  OIDC Implicit Grant Redirect With Consent | 100 | Get tokens | 0 | 25.95 | 1745.67 | 1221.07 | 4703 | 99.07 |
|  OIDC Implicit Grant Redirect With Consent | 100 | Send request to authorize end point | 0 | 26 | 820.5 | 613.17 | 2447 | 99.07 |
|  OIDC Implicit Grant Redirect With Consent | 150 | Common Auth Login HTTP Request | 0 | 26.12 | 838.17 | 618.77 | 2591 | 99.08 |
|  OIDC Implicit Grant Redirect With Consent | 150 | Common Auth Login HTTP Request Redirect | 0 | 26.15 | 1115.9 | 876.71 | 3663 | 99.08 |
|  OIDC Implicit Grant Redirect With Consent | 150 | Get tokens | 0 | 26.09 | 2477.66 | 1709.07 | 6591 | 99.08 |
|  OIDC Implicit Grant Redirect With Consent | 150 | Send request to authorize end point | 0 | 26.09 | 1296.18 | 975.31 | 3823 | 99.08 |
|  OIDC Implicit Grant Redirect With Consent | 300 | Common Auth Login HTTP Request | 0 | 26.49 | 1640.98 | 1201.67 | 5055 | 99.01 |
|  OIDC Implicit Grant Redirect With Consent | 300 | Common Auth Login HTTP Request Redirect | 0 | 26.48 | 2275.18 | 1777.66 | 6975 | 99.01 |
|  OIDC Implicit Grant Redirect With Consent | 300 | Get tokens | 0 | 26.5 | 4601.37 | 2979.33 | 11199 | 99.01 |
|  OIDC Implicit Grant Redirect With Consent | 300 | Send request to authorize end point | 0 | 26.43 | 2798.95 | 2140.2 | 8127 | 99.01 |
|  OIDC Implicit Grant Redirect With Consent | 500 | Common Auth Login HTTP Request | 0 | 26.83 | 2433.87 | 1512.12 | 6271 | 98.73 |
|  OIDC Implicit Grant Redirect With Consent | 500 | Common Auth Login HTTP Request Redirect | 0 | 26.82 | 3554.3 | 2478.08 | 9471 | 98.73 |
|  OIDC Implicit Grant Redirect With Consent | 500 | Get tokens | 0 | 26.73 | 8182.1 | 5040.14 | 16895 | 98.73 |
|  OIDC Implicit Grant Redirect With Consent | 500 | Send request to authorize end point | 0 | 26.71 | 4334.85 | 3027.52 | 11007 | 98.73 |
|  OIDC Password Grant Type | 50 | GetToken_Password_Grant | 0 | 43.11 | 1158.03 | 775.73 | 2863 | 99.39 |
|  OIDC Password Grant Type | 100 | GetToken_Password_Grant | 0 | 42.34 | 2351.66 | 1695.09 | 6591 | 99.36 |
|  OIDC Password Grant Type | 150 | GetToken_Password_Grant | 0 | 42.25 | 3529.16 | 2510.11 | 9791 | 99.32 |
|  OIDC Password Grant Type | 300 | GetToken_Password_Grant | 0 | 41.28 | 7160.56 | 4945.65 | 18047 | 99.36 |
|  OIDC Password Grant Type | 500 | GetToken_Password_Grant | 0 | 39.63 | 12314.23 | 7665.93 | 25983 | 99.14 |
|  OIDC Auth Code Request Path Authenticator With Consent | 50 | Get Authorization Code | 0 | 20.91 | 340.79 | 247.15 | 999 | 99.2 |
|  OIDC Auth Code Request Path Authenticator With Consent | 50 | Get tokens | 0 | 20.88 | 1201.54 | 814.43 | 2831 | 99.2 |
|  OIDC Auth Code Request Path Authenticator With Consent | 50 | Send request to authorize end poiont | 0 | 20.91 | 846.96 | 561.33 | 2047 | 99.2 |
|  OIDC Auth Code Request Path Authenticator With Consent | 100 | Get Authorization Code | 0 | 20.35 | 710.69 | 535.58 | 2239 | 99.21 |
|  OIDC Auth Code Request Path Authenticator With Consent | 100 | Get tokens | 0 | 20.33 | 2422.75 | 1617.23 | 5823 | 99.21 |
|  OIDC Auth Code Request Path Authenticator With Consent | 100 | Send request to authorize end poiont | 0 | 20.36 | 1780.03 | 1180.8 | 4543 | 99.21 |
|  OIDC Auth Code Request Path Authenticator With Consent | 150 | Get Authorization Code | 0 | 20.61 | 1095.81 | 865.89 | 3615 | 99.1 |
|  OIDC Auth Code Request Path Authenticator With Consent | 150 | Get tokens | 0 | 20.57 | 3435.85 | 2394.15 | 8703 | 99.1 |
|  OIDC Auth Code Request Path Authenticator With Consent | 150 | Send request to authorize end poiont | 0 | 20.59 | 2720.86 | 1862.85 | 7007 | 99.1 |
|  OIDC Auth Code Request Path Authenticator With Consent | 300 | Get Authorization Code | 0 | 19.45 | 2438.95 | 1761.63 | 6943 | 99.06 |
|  OIDC Auth Code Request Path Authenticator With Consent | 300 | Get tokens | 0 | 19.53 | 6987.86 | 4391.45 | 15423 | 99.06 |
|  OIDC Auth Code Request Path Authenticator With Consent | 300 | Send request to authorize end poiont | 0 | 19.45 | 5842.04 | 3701.22 | 13503 | 99.06 |
|  OIDC Auth Code Request Path Authenticator With Consent | 500 | Get Authorization Code | 0.09 | 19.19 | 3658.69 | 3775.58 | 8895 | 98.86 |
|  OIDC Auth Code Request Path Authenticator With Consent | 500 | Get tokens | 0 | 18.84 | 12996.35 | 10893.17 | 63487 | 98.86 |
|  OIDC Auth Code Request Path Authenticator With Consent | 500 | Send request to authorize end poiont | 0.06 | 19.25 | 8554.15 | 6760.16 | 18559 | 98.86 |
|  SAML2 SSO Redirect Binding | 50 | Identity Provider Login | 0 | 139.17 | 237.08 | 69.35 | 427 | 97.24 |
|  SAML2 SSO Redirect Binding | 50 | Initial SAML Request | 0 | 139.17 | 121.17 | 47.71 | 257 | 97.24 |
|  SAML2 SSO Redirect Binding | 100 | Identity Provider Login | 0 | 139.25 | 476.77 | 153.32 | 867 | 97.06 |
|  SAML2 SSO Redirect Binding | 100 | Initial SAML Request | 0 | 139.3 | 240.32 | 107.52 | 567 | 97.06 |
|  SAML2 SSO Redirect Binding | 150 | Identity Provider Login | 0 | 124.87 | 783.35 | 403.63 | 2719 | 97.25 |
|  SAML2 SSO Redirect Binding | 150 | Initial SAML Request | 0 | 124.96 | 415.91 | 281.95 | 1679 | 97.25 |
|  SAML2 SSO Redirect Binding | 300 | Identity Provider Login | 0 | 52.23 | 3539.32 | 2037.66 | 8127 | 98.3 |
|  SAML2 SSO Redirect Binding | 300 | Initial SAML Request | 0 | 52.28 | 2172.12 | 1473.47 | 6111 | 98.3 |
|  SAML2 SSO Redirect Binding | 500 | Identity Provider Login | 0 | 53.28 | 5848.1 | 3169.35 | 11647 | 98.15 |
|  SAML2 SSO Redirect Binding | 500 | Initial SAML Request | 0 | 53.36 | 3451.41 | 2081.84 | 8031 | 98.15 |
