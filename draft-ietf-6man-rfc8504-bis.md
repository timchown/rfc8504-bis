---
v: 3
docname: draft-clw-6man-rfc8504-bis-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
category: bcp
area: "Internet"
workgroup: "IPv6 Maintenance"
obsoletes: 8504
venue:
  group: "IPv6 Maintenance"
  type: "Working Group"
  mail: "ipv6@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/ipv6/"
  github: "timchown/rfc8504-bis"
  latest: "https://timchown.github.io/rfc8504-bis/draft-clw-6man-rfc8504-bis.html"

seriesno: '220'
pi:
  toc: 'yes'
  tocdepth: '3'
  symrefs: 'yes'
  sortrefs: 'yes'
  compact: 'yes'
  subcompact: 'no'
  rfcprocack: 'yes'

title: IPv6 Node Requirements
area: Internet
workgroup: "IPv6 Maintenance"
kw: IPv6

author:
- name: Tim Chown
  org: Jisc
  street: Lumen House, Library Avenue
  city: Harwell Oxford, Didcot
  code: OX11 0SG
  country: United Kingdom
  email: tim.chown@jisc.ac.uk
- name: John Loughney
  org: Intel
  city: Santa Clara, CA
  country: United States of America
  phone: ''
  email: john.loughney@gmail.com
- name: Timothy Winters
  org: QA Cafe
  city: Dover
  region: NH
  country: United States of America
  email: tim@qacafe.com

normative:
  RFC1034:
  RFC1035:
  RFC2710:
  RFC2711:
  RFC2863:
  RFC3168:
  RFC3411:
  RFC3596:
  RFC3810:
  RFC4033:
  RFC4034:
  RFC4035:
  RFC4213:
  RFC4291:
  RFC4292:
  RFC4293:
  RFC4301:
  RFC4303:
  RFC4311:
  RFC4443:
  RFC4607:
  RFC4632:
  RFC4861:
  RFC4862:
  RFC5095:
  RFC5453:
  RFC5722:
  RFC5790:
  RFC5942:
  RFC5952:
  RFC6241:
  RFC6437:
  RFC6564:
  RFC6724:
  RFC6762:
  RFC6763:
  RFC6775:
  RFC6891:
  RFC6946:
  RFC7045:
  RFC7048:
  RFC7112:
  RFC7217:
  RFC7296:
  RFC7527:
  RFC7559:
  RFC7608:
  RFC8028:
  RFC8040:
  RFC8064:
  RFC8106:
  RFC8200:
  RFC8201:
  RFC8221:
  RFC8247:
  RFC8343:
  RFC8344:
  RFC8415:
  RFC8981:
  RFC9131:
informative:
  RFC0793:
  RFC2205:
  RFC2464:
  RFC2491:
  RFC2590:
  RFC2874:
  RFC2923:
  RFC3146:
  RFC3363:
  RFC3493:
  RFC3542:
  RFC3646:
  RFC3678:
  RFC4191:
  RFC4294:
  RFC4302:
  RFC4338:
  RFC4380:
  RFC4429:
  RFC4584:
  RFC4821:
  RFC4884:
  RFC4890:
  RFC4919:
  RFC4944:
  RFC5014:
  RFC5072:
  RFC5121:
  RFC6275:
  RFC6563:
  RFC6980:
  RFC7084:
  RFC7123:
  RFC7371:
  RFC7421:
  RFC7721:
  RFC7739:
  RFC7772:
  RFC7844:
  RFC7934:
  RFC8087:
  RFC8096:
  RFC8273:
  RFC8781:
  RFC7050:
  POSIX:
    target: https://ieeexplore.ieee.org/document/8277153
    title: Information Technology -- Portable Operating System Interface (POSIX(R))
      Base Specifications, Issue 7
    author:
    - org: IEEE
    date: 2018-01
    seriesinfo:
      IEEE Std: 1003.1-2017
      'DOI:': 10.1109/IEEESTD.2018.8277153
  USGv6:
    target: https://www.nist.gov/programs-projects/usgv6-program
    title: A Profile for IPv6 in the U.S. Government - Version 1.0
    author:
    - org: National Institute of Standards and Technology
    date: 2008-07
    seriesinfo:
      NIST: SP500-267

--- abstract


This document defines requirements for IPv6 nodes.  It is
expected that IPv6 will be deployed in a wide range of devices and
situations.  Specifying the requirements for IPv6 nodes allows
IPv6 to function well and interoperate in a large number of
situations and deployments.

This document obsoletes RFC 8504, and in turn RFC 6434 and its predecessor, RFC 4294.

--- middle

# Introduction

This document defines common functionality required by both
IPv6 hosts and routers.  Many IPv6 nodes will implement optional
or additional features, but this document collects and summarizes
requirements from other published Standards Track documents in one
place.

This document tries to avoid discussion of protocol details
and references RFCs for this purpose.  This document is intended
to be an applicability statement and to provide guidance as to which
IPv6 specifications should be implemented in the general case and
which specifications may be of interest to specific deployment
scenarios. This document does not update any individual protocol
document RFCs.

Although this document points to different specifications, it
should be noted that in many cases, the granularity of a
particular requirement will be smaller than a single specification,
as many specifications define multiple, independent pieces, some
of which may not be mandatory. In addition, most specifications
define both client and server behavior in the same specification,
while many implementations will be focused on only one of those
roles.

This document defines a minimal level of requirement needed
for a device to provide useful Internet service and considers a
broad range of device types and deployment scenarios. Because of
the wide range of deployment scenarios, the minimal requirements
specified in this document may not be sufficient for all
deployment scenarios. It is perfectly reasonable (and indeed
expected) for other profiles to define additional or stricter
requirements appropriate for specific usage and deployment
environments. As an example, this document does not mandate that all
clients support DHCP, but some deployment scenarios may deem
it appropriate to make such a requirement. As another example,
NIST has defined profiles for specialized requirements for IPv6
in target environments (see {{USGv6}}).

As it is not always possible for an implementer to know the
exact usage of IPv6 in a node, an overriding requirement for IPv6
nodes is that they should adhere to Jon Postel's Robustness
Principle: "Be conservative in what you do, be liberal in what you accept
from others" {{RFC0793}}.

## Scope of This Document

IPv6 covers many specifications.  It is intended that IPv6
will be deployed in many different situations and environments.
Therefore, it is important to develop requirements for IPv6
nodes to ensure interoperability.


## Description of IPv6 Nodes

From "Internet Protocol, Version 6 (IPv6) Specification" {{RFC8200}}, we
have the following definitions:

~~~~
IPv6 node   - a device that implements IPv6.
IPv6 router - a node that forwards IPv6 packets not explicitly
              addressed to itself.
IPv6 host   - any IPv6 node that is not a router.
~~~~


# Requirements Language

{::boilerplate bcp14-tagged}


# Abbreviations Used in This Document

~~~~
AH    Authentication Header
DAD   Duplicate Address Detection
ESP   Encapsulating Security Payload
ICMP  Internet Control Message Protocol
IKE   Internet Key Exchange
MIB   Management Information Base
MLD   Multicast Listener Discovery
MTU   Maximum Transmission Unit
NA    Neighbor Advertisement
NBMA  Non-Broadcast Multi-Access
ND    Neighbor Discovery
NS    Neighbor Solicitation
NUD   Neighbor Unreachability Detection
PPP   Point-to-Point Protocol
~~~~


# Sub-IP Layer

An IPv6 node MUST include support for one or more IPv6
link-layer specifications.  Which link-layer specifications an
implementation should include will depend upon what link layers
are supported by the hardware available on the system.  It is
possible for a conformant IPv6 node to support IPv6 on some of its
interfaces and not on others.

As IPv6 is run over new Layer 2 technologies, it is expected
that new specifications will be issued.  We list here some of
the Layer 2 technologies for which an IPv6 specification has been developed.
It is provided for informational purposes only and may
not be complete.

- Transmission of IPv6 Packets over Ethernet Networks {{RFC2464}}
- Transmission of IPv6 Packets over Frame Relay Networks Specification
  {{RFC2590}}
- Transmission of IPv6 Packets over IEEE 1394 Networks {{RFC3146}}
- Transmission of IPv6, IPv4, and Address Resolution Protocol (ARP)
  Packets over Fibre Channel {{RFC4338}}
- Transmission of IPv6 Packets over IEEE 802.15.4 Networks {{RFC4944}}
- Transmission of IPv6 via the IPv6 Convergence Sublayer over IEEE
  802.16 Networks {{RFC5121}}
- IP version 6 over PPP {{RFC5072}}

In addition to traditional physical link layers, it is also
possible to tunnel IPv6 over other protocols. Examples
include:

- Teredo: Tunneling IPv6 over UDP through Network Address Translations
  (NATs) {{RFC4380}}
- Basic Transition Mechanisms for IPv6 Hosts and Routers (see {{Section
  3 of RFC4213}})


# IP Layer

## Internet Protocol Version 6 - RFC 8200

The Internet Protocol version 6 is specified in {{RFC8200}}.  This specification MUST be supported.

The node MUST follow the packet transmission rules in RFC 8200.

All conformant IPv6 implementations MUST be
capable of sending and receiving IPv6 packets; forwarding
functionality MAY be supported.
Nodes MUST always be able to send, receive, and process
Fragment headers.

IPv6 nodes MUST NOT create
overlapping fragments.  Also, when reassembling an IPv6
datagram, if one or more of its constituent fragments is
determined to be an overlapping fragment, the entire datagram
(and any constituent fragments) MUST be silently discarded.
See Section 4.5 of {{RFC8200}} for more information.

As recommended in Section 4.5 of {{RFC8200}}, nodes MUST NOT
generate atomic fragments, i.e., where the fragment is a whole datagram.
As per {{RFC6946}}, if a receiving node reassembling
a datagram encounters an atomic fragment,
it should be processed as a fully reassembled packet, and
any other fragments that match this packet should be processed independently.

To mitigate a variety of potential attacks,
nodes SHOULD avoid using predictable Fragment Identification values
in Fragment headers, as discussed in {{RFC7739}}.

All nodes SHOULD support the setting and use of the IPv6 Flow
Label field as defined in the IPv6 Flow Label specification {{RFC6437}}.
Forwarding nodes such as routers and load distributors
MUST NOT depend only on Flow Label values being uniformly
distributed.  It is RECOMMENDED that source hosts support the flow
label by setting the Flow Label field for all packets of a given
flow to the same value chosen from an approximation to a discrete
uniform distribution.


## Support for IPv6 Extension Headers

RFC 8200 specifies extension headers and the processing for
these headers.

Extension headers (except for the Hop-by-Hop Options header) are not
processed, inserted, or deleted by any node along a packet's delivery
path, until the packet reaches the node (or each of the set of nodes,
in the case of multicast) identified in the Destination Address field
of the IPv6 header.

Any unrecognized extension headers or options MUST be
processed as described in RFC 8200. Note that where
{{Section 4 of RFC8200}}
refers to the action to be taken when a Next Header value
in the current header is not recognized by a node, that action
applies whether the value is an unrecognized extension
header or an unrecognized upper-layer protocol (ULP).

An IPv6 node MUST be able to process these extension headers.  An
exception is Routing Header type 0 (RH0), which was deprecated
by {{RFC5095}} due to security concerns and
which MUST be treated as an unrecognized routing type.

Further, {{RFC7045}} adds specific requirements for
the processing of extension headers, in particular that any forwarding
node along an IPv6 packet's path, which forwards the packet for
any reason, SHOULD do so regardless of any extension headers
that are present.

As per RFC 8200, when a node fragments an IPv6 datagram,
it MUST include the entire IPv6 Header Chain in the first fragment.
The Per-Fragment headers MUST
consist of the IPv6 header plus any extension headers that MUST be
processed by nodes en route to the destination,
that is, all headers up to and including the Routing
header if present, else the Hop-by-Hop Options header if present,
else no extension headers.  On reassembly,
if the first fragment does not include all headers through an
upper-layer header, then that fragment SHOULD be discarded and
an ICMP Parameter Problem, Code 3, message SHOULD be sent to
the source of the fragment, with the Pointer field set to zero.
See {{RFC7112}} for a discussion of why oversized
IPv6 Extension Header Chains are avoided.

Defining new IPv6 extension headers is not recommended, unless there
are no existing IPv6 extension headers that can be used by specifying
a new option for that IPv6 extension header.  A proposal to specify a
new IPv6 extension header MUST include a detailed technical
explanation of why an existing IPv6 extension header can not be used
for the desired new function, and in such cases, it needs to follow the format
described in {{Section 8 of RFC8200}}.  For further background
reading on this topic, see {{RFC6564}}.


## Protecting a Node from Excessive Extension Header Options

As per RFC 8200, end hosts are expected to process all extension headers,
destination options, and hop-by-hop options in a packet. Given that
the only limit on the number and size of extension headers is the MTU,
the processing of received packets could be considerable. It is also
conceivable that a long chain of extension headers might be used as a
form of denial-of-service attack. Accordingly, a host may place limits
on the number and sizes of extension headers and options it is willing
to process.

A host MAY limit the number of consecutive PAD1 options in destination
options or hop-by-hop options to 7.
In this case, if there are more than 7
consecutive PAD1 options present, the packet MAY be
silently discarded. The rationale is that if padding of 8 or more
bytes is required, then the PADN option SHOULD be used.

A host MAY limit the number of bytes in a PADN option to be less than
8. In such a case, if a PADN option is present that has a length
greater than 7, the packet SHOULD be silently discarded. The
rationale for this guideline is that the purpose of padding is for
alignment and 8 bytes is the maximum alignment used in IPv6.

A host MAY disallow unknown options in destination options or
hop-by-hop options. This SHOULD be configurable where the default is
to accept unknown options and process them per {{RFC8200}}. If a packet
with unknown options is received and the host is configured to
disallow them, then the packet SHOULD be silently discarded.

A host MAY impose a limit on the maximum number of non-padding options
allowed in the destination options and hop-by-hop extension headers. If
this feature is supported, the maximum number SHOULD be configurable,
and the default value SHOULD be set to 8. The limits for
destination options and hop-by-hop options may be separately
configurable. If a packet is received and the number of destination or
hop-by-hop options exceeds the limit, then the packet SHOULD be
silently discarded.

A host MAY impose a limit on the maximum length of Destination Options
or Hop-by-Hop Options extension headers. This value SHOULD be
configurable, and the default is to accept options of any length. If a
packet is received and the length of the Destination or Hop-by-Hop Options
extension header exceeds the length limit, then the packet SHOULD be
silently discarded.


## Neighbor Discovery for IPv6 - RFC 4861 {#ND}

Neighbor Discovery is defined in {{RFC4861}}; the
definition was updated by {{RFC5942}}. Neighbor Discovery
MUST be supported with the noted exceptions below.  RFC 4861 states:

>
Unless specified otherwise (in a document that covers operating IP
over a particular link type) this document applies to all link types.
However, because ND uses link-layer multicast for some of its
services, it is possible that on some link types (e.g., Non‑Broadcast
Multi-Access (NBMA) links), alternative protocols or mechanisms to
implement those services will be specified (in the appropriate
document covering the operation of IP over a particular link type).
The services described in this document that are not directly
dependent on multicast, such as Redirects, Next-hop determination,
Neighbor Unreachability Detection, etc., are expected to be provided
as specified in this document.
The details of how one uses ND on
NBMA links are addressed in {{RFC2491}}.


Some detailed analysis of Neighbor Discovery follows:

Router Discovery is how hosts locate routers that reside on
an attached link.  Hosts MUST support Router Discovery
functionality.

Prefix Discovery is how hosts discover the set of address
prefixes that define which destinations are on-link for an
attached link. Hosts MUST support Prefix Discovery.

Hosts MUST also implement Neighbor Unreachability Detection
(NUD) for all paths between hosts and neighboring nodes.  NUD is
not required for paths between routers.  However, all nodes MUST
respond to unicast Neighbor Solicitation (NS) messages.

 {{RFC7048}} discusses NUD, in particular cases
where it behaves too impatiently. It states that if a node
transmits more than a certain number of packets, then it
SHOULD use the exponential backoff of the retransmit timer,
up to a certain threshold point.

Hosts MUST support the sending of Router Solicitations and
the receiving of Router Advertisements (RAs).  The ability to
understand individual RA options is dependent
on supporting the functionality making use of the particular
option.

 {{RFC7559}} discusses packet loss resiliency
for Router Solicitations and requires that nodes MUST use
a specific exponential backoff algorithm for retransmission of Router
Solicitations.

All nodes MUST support the sending and receiving of Neighbor
Solicitation (NS) and Neighbor Advertisement (NA) messages.  NS
and NA messages are required for Duplicate Address Detection
(DAD).

Hosts SHOULD support the processing of Redirect
functionality.  Routers MUST support the sending of Redirects,
though not necessarily for every individual packet (e.g., due to
rate limiting). Redirects are only useful on networks supporting
hosts. In core networks dominated by routers, Redirects are
typically disabled.  The sending of Redirects SHOULD be disabled
by default on routers intended to be deployed on core networks. They MAY
be enabled by default on routers intended to support hosts on edge networks.

As specified in {{RFC6980}}, nodes MUST NOT employ IPv6 fragmentation
for sending any of the following Neighbor Discovery and SEcure
Neighbor Discovery messages: Neighbor Solicitation, Neighbor
Advertisement, Router Solicitation, Router Advertisement, Redirect, or
Certification Path Solicitation.
Nodes MUST silently ignore any of these messages on receipt if
fragmented.
See RFC 6980 for details and motivation.

"IPv6 Host-to-Router Load Sharing" {{RFC4311}} includes additional
recommendations on how to select from a set of available routers.
{{RFC4311}} SHOULD be supported.

## IPv6 Router Advertisement Flags Option - RFC 5175

Router Advertisements include an 8-bit field of single-bit
Router Advertisement flags.  The Router Advertisement Flags
Option extends the number of available flag bits by 48 bits. At
the time of this writing, 6 of the original 8 single-bit flags have
been assigned, while 2 remain available for future
assignment. No flags have been defined that make use of the new
option; thus, strictly speaking, there is no requirement to
implement the option today. However, implementations that are
able to pass unrecognized options to a higher-level entity that
may be able to understand them (e.g., a user-level process using
a "raw socket" facility) MAY take steps to handle the option in
anticipation of a future usage.


## Path MTU Discovery and Packet Size

### Path MTU Discovery - RFC 8201

"Path MTU Discovery for IP version 6" {{RFC8201}} SHOULD be
supported.  From {{RFC8200}}:

>
It is strongly recommended that IPv6 nodes implement
Path MTU Discovery {{RFC8201}}, in order to
discover and
take advantage of path MTUs greater than 1280 octets.
However, a minimal IPv6 implementation (e.g., in a boot
ROM) may simply restrict itself to sending packets no
larger than 1280 octets, and omit implementation of Path
MTU Discovery.


The rules in {{RFC8200}} and {{RFC5722}} MUST be followed for packet
fragmentation and reassembly.

As described in RFC 8201,
nodes implementing Path MTU Discovery and sending packets larger than
the IPv6 minimum link MTU are susceptible to problematic connectivity
if ICMPv6 messages are blocked or not transmitted.  For
example, this will result in connections that complete the TCP
three-way handshake correctly but then hang when data is transferred.  This
state is referred to as a black-hole connection {{RFC2923}}.  Path MTU
Discovery relies on ICMPv6 Packet Too Big (PTB) to determine the MTU
of the path (and thus these MUST NOT be filtered, as per the
recommendation in {{RFC4890}}).

An alternative to Path MTU Discovery defined in RFC 8201 can be
found in {{RFC4821}}, which defines a method for Packetization
Layer Path MTU Discovery (PLPMTUD) designed for use over paths where
delivery of ICMPv6 messages to a host is not assured.


### Minimum MTU Considerations

While an IPv6 link MTU can be set to 1280 bytes,
it is recommended that for IPv6 UDP in particular,
which includes DNS operation, the sender use a
large MTU if they can, in order to avoid gratuitous
fragmentation-caused packet drops.



## ICMP for the Internet Protocol Version 6 (IPv6) - RFC 4443

ICMPv6 {{RFC4443}} MUST be supported. "Extended
ICMP to Support Multi-Part Messages" {{RFC4884}} MAY be supported.


## Default Router Preferences and More-Specific Routes - RFC 4191

"Default Router Preferences and More-Specific Routes" {{RFC4191}}
provides support for nodes attached to
multiple (different) networks, each providing routers that
advertise themselves as default routers via Router
Advertisements. In some scenarios, one router may provide
connectivity to destinations that the other router does not, and
choosing the "wrong" default router can result in reachability
failures. In order to resolve this scenario, IPv6 nodes MUST implement
{{RFC4191}} and MUST implement the Type C host role defined in RFC 4191.


## First-Hop Router Selection - RFC 8028

In multihomed scenarios, where a host has more than one prefix,
each allocated by an upstream network that is assumed to implement
BCP 38 ingress filtering, the host may have multiple routers to
choose from.

Hosts that may be deployed in such multihomed environments
SHOULD follow the guidance given in {{RFC8028}}.


## Multicast Listener Discovery (MLD) for IPv6 - RFC 3810 {#mld}

Nodes that need to join multicast groups MUST support MLDv2
{{RFC3810}}. MLD is needed by any node that is
expected to receive and process multicast traffic; in particular,
MLDv2 is required for support for source-specific multicast (SSM) as
per {{RFC4607}}.

Previous versions of this specification only required MLDv1 {{RFC2710}}
to be implemented
on all nodes.  Since participation of any
MLDv1-only nodes on a link require that all other nodes on the link then
operate in version 1 compatibility mode, the requirement to support MLDv2
on all nodes was upgraded to a MUST. Further, SSM is now the preferred
multicast distribution method, rather than Any-Source Multicast (ASM).

Note that Neighbor Discovery (as used on most link types -- see {{ND}})
depends on multicast and requires that nodes join Solicited Node
multicast addresses.


## Explicit Congestion Notification (ECN) - RFC 3168

An ECN-aware router sets a mark in the IP header in order to signal
impending congestion, rather than dropping a packet. The receiver of
the packet echoes the congestion indication to the sender, which can then
reduce its transmission rate as if it detected a dropped packet.

Nodes SHOULD support ECN {{RFC3168}} by implementing an interface
for the upper layer to access and by setting the ECN bits in the IP header.
The benefits of using ECN are documented in {{RFC8087}}.



# Addressing and Address Configuration

## IP Version 6 Addressing Architecture - RFC 4291

The IPv6 Addressing Architecture {{RFC4291}} MUST be supported.

The current IPv6 Address Architecture is based on a 64-bit boundary for subnet
prefixes.
The reasoning behind this decision is documented in {{RFC7421}}.

Implementations MUST also support the multicast flag updates
documented in {{RFC7371}}.


## Host Address Availability Recommendations

Hosts may be configured with addresses through a variety of methods,
including Stateless Address Autoconfiguration (SLAAC), DHCPv6, or manual
configuration.

{{RFC7934}} recommends that networks provide general-purpose end hosts
with multiple global IPv6 addresses when they attach, and it describes
the benefits of and the options for doing so.
Routers SHOULD support {{RFC7934}} for assigning multiple addresses to a
host.
A host SHOULD support assigning multiple addresses as described in
{{RFC7934}}.

Nodes SHOULD support the capability to be assigned a prefix per host as
documented in {{RFC8273}}.
Such an approach can offer improved host
isolation and enhanced subscriber management on shared network segments.


## IPv6 Stateless Address Autoconfiguration - RFC 4862

Hosts MUST support IPv6 Stateless Address Autoconfiguration.
It is RECOMMENDED, as described in {{RFC8064}}, that unless there
is a specific requirement for Media Access Control (MAC) addresses to be
embedded in
an Interface Identifier (IID), nodes follow the procedure in {{RFC7217}} to generate SLAAC-based
addresses, rather than use {{RFC4862}}.
Addresses generated using the method described in {{RFC7217}} will be the same whenever a given device (re)appears on the
same subnet (with a specific IPv6 prefix), but the IID will vary on
each subnet visited.

Nodes that are routers MUST be able to generate link-local
addresses as described in {{RFC4862}}.

From RFC 4862:

>
<!-- Begin DNE text -->The autoconfiguration process specified in this document
applies only to hosts and not routers.  Since host
autoconfiguration uses information advertised by routers,
routers will need to be configured by some other means.
However, it is expected that routers will generate link-local
addresses using the mechanism described in this document.  In
addition, routers are expected to successfully pass the
Duplicate Address Detection procedure described in this
document on all addresses prior to assigning them to an
interface.


All nodes MUST implement Duplicate Address Detection. Quoting
from {{Section 5.4 of RFC4862}}:

>
Duplicate Address Detection MUST
be performed on all unicast addresses prior to assigning them
to an interface, regardless of whether they are obtained
through stateless autoconfiguration, DHCPv6, or manual
configuration, with the following exceptions \[noted therein].


"Optimistic Duplicate Address Detection (DAD) for
IPv6" {{RFC4429}} specifies a mechanism to reduce
delays associated with generating addresses via Stateless
Address Autoconfiguration {{RFC4862}}.  RFC 4429
was developed in conjunction with Mobile IPv6 in order to reduce
the time needed to acquire and configure addresses as devices
quickly move from one network to another, and it is desirable to
minimize transition delays.  For general purpose devices, RFC 4429 remains
optional at this time.

 {{RFC7527}} discusses enhanced DAD and describes an
algorithm to automate the detection of looped-back IPv6 ND messages
used by DAD. Nodes SHOULD implement this behavior where such
detection is beneficial.


## Privacy Extensions for Address Configuration in IPv6 - RFC 8981

A node using Stateless Address
Autoconfiguration {{RFC4862}} to form a globally
unique IPv6 address that uses its MAC address to generate the IID
will see that the IID remains the same on any visited
network, even though the network prefix part changes.
Thus, it is possible for a third-party device to track the activities of
the node they
communicate, as that node moves around the network.  Privacy Extensions
for Stateless Address
Autoconfiguration {{RFC8981}} address this
concern by allowing nodes to configure an additional temporary address
where the IID is effectively randomly generated.  Privacy addresses
are then used as source addresses for new communications initiated by the
node.

General issues regarding privacy issues for IPv6 addressing are discussed
in {{RFC7721}}.

RFC 8981 SHOULD be supported.  In some scenarios,
such as dedicated servers in a data
center, it provides limited or no benefit, or it may complicate network management.
Thus, devices implementing this specification MUST provide a way for the
end user to explicitly enable or disable the use of such temporary
addresses.

Note that RFC 8981 can be used independently of traditional SLAAC or independently
of SLAAC that is based on RFC 7217.

Implementers of RFC 8981 should be aware that certain
addresses are reserved and should not be chosen for use as
temporary addresses. Consult "Reserved IPv6 Interface
Identifiers" {{RFC5453}} for more details.


## Stateful Address Autoconfiguration (DHCPv6) - RFC 8415 {#stateful1}

DHCPv6 {{RFC8415}} can be used to obtain and
configure addresses. In general, a network may provide for the
configuration of addresses through SLAAC,
DHCPv6, or both.  There will be a wide range of IPv6 deployment
models and differences in address assignment requirements,
some of which may require DHCPv6 for stateful address assignment.
Consequently, all hosts SHOULD implement address configuration
via DHCPv6.

In the absence of observed Router Advertisement messages, IPv6 nodes
MAY initiate DHCP to obtain IPv6 addresses
and other configuration information, as described in {{Section
5.5.2 of RFC4862}}.

Where devices are likely to be carried by users and attached
to multiple visited networks, DHCPv6 client
anonymity profiles SHOULD be supported as described in {{RFC7844}} to minimize the disclosure of identifying information.
{{Section 5 of RFC7844}} describes operational considerations on the use of
such anonymity profiles.


## Default Address Selection for IPv6 - RFC 6724

IPv6 nodes will invariably have multiple addresses configured simultaneously
and thus will need to choose which addresses to use for which communications.
The rules specified in the Default Address Selection for
IPv6 document {{RFC6724}} MUST be implemented. {{RFC8028}} updates Rule 5.5 from {{RFC6724}}; implementations
SHOULD implement this rule.



# DNS

DNS is described in {{RFC1034}}, {{RFC1035}}, {{RFC3363}}, and {{RFC3596}}.  Not all nodes will need to resolve names;
those that will never need to resolve DNS names do not need to
implement resolver functionality.  However, the ability to
resolve names is a basic infrastructure capability on which
applications rely, and most nodes will need to provide
support.  All nodes SHOULD implement stub-resolver {{RFC1034}} functionality, as in Section 5.3.1 of {{RFC1034}}, with support for:



-
: AAAA type Resource Records {{RFC3596}};


-
: reverse addressing in ip6.arpa using PTR records {{RFC3596}}; and


-
: Extension Mechanisms for DNS (EDNS(0)) {{RFC6891}} to allow for DNS packet sizes larger than 512 octets.


Those nodes are RECOMMENDED to support DNS security extensions {{RFC4033}}  {{RFC4034}}  {{RFC4035}}.

A6 Resource Records {{RFC2874}} are classified as Historic per {{RFC6563}}.  These were defined with Experimental status in {{RFC3363}}.


# Configuring Non-address Information {#OtherConfig}

## DHCP for Other Configuration Information

DHCP {{RFC8415}} specifies a mechanism for IPv6 nodes to obtain
address configuration information (see {{stateful1}}) and to
obtain additional (non-address) configuration.  If a host
implementation supports applications or other protocols that
require configuration that is only available via DHCP, hosts
SHOULD implement DHCP. For specialized devices on which no
such configuration need is present, DHCP may not be
necessary.

An IPv6 node can use the subset of DHCP (described in {{RFC8415}}) to obtain other configuration
information.

If an IPv6 node implements DHCP, it MUST implement the DNS options {{RFC3646}} as most deployments will expect that these options are available.


## Router Advertisements and Default Gateway

There is no defined DHCPv6 Gateway option.

Nodes using the Dynamic Host Configuration Protocol for
IPv6 (DHCPv6) are thus expected to determine their default router
information and on-link prefix information from received
Router Advertisements.


## IPv6 Router Advertisement Options for DNS         Configuration - RFC 8106

Router Advertisement options have historically been limited to
those that are critical to basic IPv6 functionality. Originally,
DNS configuration was not included as an RA option, and DHCP
was the recommended way to obtain DNS configuration
information. Over time, the thinking surrounding such an
option has evolved. It is now generally recognized that few
nodes can function adequately without having access to a
working DNS resolver; thus, a
Standards Track document has been published to provide this
capability {{RFC8106}}.

Implementations MUST include support for the DNS RA option {{RFC8106}}.


## DHCP Options versus Router Advertisement Options for Host Configuration

In IPv6, there are two main protocol mechanisms for
propagating configuration information to hosts: RAs and DHCP. RA options
have been
restricted to those deemed essential for basic network
functioning and for which all nodes are configured with exactly
the same information.  Examples include the Prefix Information
Options, the MTU option, etc. On the other hand, DHCP has
generally been preferred for configuration of more general
parameters and for parameters that may be client specific.
Generally speaking, however, there has been a desire
to define only one mechanism for configuring a given option,
rather than defining multiple (different) ways of configuring
the same information.

One issue with having multiple ways to configure the same
information is that interoperability suffers if a host chooses one
mechanism but the
network operator chooses a different mechanism. For "closed"
environments, where the network operator
has significant influence over what devices connect to the
network and thus what configuration mechanisms they support, the
operator may be able to ensure that a particular mechanism is
supported by all connected hosts. In more open environments,
however, where arbitrary devices may connect (e.g., a Wi-Fi
hotspot), problems can arise. To maximize interoperability in
such environments, hosts would need to implement multiple
configuration mechanisms to ensure interoperability.



# Service Discovery Protocols

Multicast DNS (mDNS) and
DNS-based Service Discovery (DNS-SD) are described in {{RFC6762}} and {{RFC6763}}, respectively.
These protocols, often collectively referred to as the
'Bonjour' protocols after their naming by Apple, provide
the means for devices to discover services within a local
link and, in the absence of a unicast DNS service, to
exchange naming information.

Where devices are to be deployed in networks where
service discovery would be beneficial, e.g., for users
seeking to discover printers or display devices, mDNS and
DNS-SD SHOULD be supported.


# IPv4 Support and Transition

IPv6 nodes MAY support IPv4.

## Transition Mechanisms

### Basic Transition Mechanisms for IPv6 Hosts and Routers - RFC 4213

If an IPv6 node implements dual stack and tunneling, then {{RFC4213}} MUST be supported.

### Support for discovery of translation prefixes

[RFC8781] describes a Neighbor Discovery option to be used in Router Advertisements (RAs) to communicate prefixes of Network Address and Protocol Translation from IPv6 clients to IPv4 servers (NAT64) to hosts. In order to support migration to and operation of IPv6-mostly and IPv6-only network environments, it is recommended that all hosts support discovery of NAT64 prefixes as described in RFC 8781.
Nodes MAY also support [RFC7050] as a fallback mechanism for NAT64 prefix discovery.


# Application Support

## Textual Representation of IPv6 Addresses - RFC 5952

Software that allows users and operators to input IPv6
addresses in text form SHOULD support "A Recommendation for
IPv6 Address Text Representation" {{RFC5952}}.


## Application Programming Interfaces (APIs)

There are a number of IPv6-related APIs. This document does
not mandate the use of any, because the choice of API does not
directly relate to on-the-wire behavior of
protocols. Implementers, however, would be advised to consider
providing a common API or reviewing existing APIs for the type
of functionality they provide to applications.

"Basic Socket Interface Extensions for IPv6" {{RFC3493}} provides IPv6 functionality used by
typical applications. Implementers should note that RFC 3493 has
been picked up and further standardized by the Portable Operating System
Interface (POSIX) {{POSIX}}.

"Advanced Sockets Application Program Interface (API) for
IPv6" {{RFC3542}} provides access to
advanced IPv6 features needed by diagnostic and other
more specialized applications.

"IPv6 Socket API for Source Address Selection" {{RFC5014}} provides facilities that allow an
application to override the default Source Address Selection
rules of {{RFC6724}}.

"Socket Interface Extensions for Multicast Source Filters" {{RFC3678}} provides support for expressing source
filters on multicast group memberships.

"Extension to Sockets API for Mobile IPv6" {{RFC4584}} provides application support for
accessing and enabling Mobile IPv6 {{RFC6275}} features.

# Security {#sec}

This section describes the security specification for IPv6
nodes.

Achieving security in practice is a complex undertaking.
Operational procedures, protocols, key distribution mechanisms,
certificate management approaches, etc., are all components that
impact the level of security actually achieved in practice. More
importantly, deficiencies or a poor fit in any one individual
component can significantly reduce the overall effectiveness of a
particular security approach.

IPsec can provide either end-to-end security between nodes
or channel security (for example, via a site-to-site IPsec
VPN), making it possible to provide secure communication for all (or a subset
of) communication flows at the IP layer between pairs of Internet
nodes.  IPsec has two standard operating modes: Tunnel-mode and Transport-mode.
In Tunnel-mode, IPsec provides network-layer security and protects an entire
IP packet
by encapsulating the original IP packet and then prepending a new IP header.
In Transport-mode, IPsec provides security for the transport layer (and above)
by
encapsulating only the transport-layer (and above) portion of the IP packet
(i.e., without adding
a second IP header).

Although IPsec can be used with manual keying in some cases,
such usage has limited applicability and is not recommended.

A range of security technologies and approaches proliferate
today (e.g., IPsec, Transport Layer Security (TLS), Secure SHell (SSH), TLS
VPNS, etc.).
No single approach has emerged as
an ideal technology for all needs and environments. Moreover, IPsec
is not viewed as the ideal security technology in all cases and is
unlikely to displace the others.

Previously, IPv6 mandated implementation of IPsec and
recommended the key-management approach of IKE. RFC 6434 updated that recommendation
by making support of the IPsec
architecture {{RFC4301}} a SHOULD for all IPv6 nodes, and this document retains that recommendation.
Note that
the IPsec Architecture requires the
implementation of both manual and automatic key management (e.g., {{Section
4.5 of RFC4301}}).
Currently, the recommended automated key-management protocol to
implement is IKEv2 {{RFC7296}}.

This document recognizes that there exists a range of device
types and environments where approaches to security other than
IPsec can be justified. For example, special-purpose devices may
support only a very limited number or type of applications, and an
application-specific security approach may be sufficient for
limited management or configuration capabilities. Alternatively,
some devices may run on extremely constrained hardware (e.g.,
sensors) where the full IPsec Architecture is not justified.

Because most common platforms now support IPv6 and have it
enabled by default, IPv6 security is an issue for networks
that are ostensibly IPv4 only; see {{RFC7123}} for guidance on this area.

## Requirements

"Security Architecture for the Internet Protocol" {{RFC4301}} SHOULD be supported by all IPv6
nodes. Note that the IPsec Architecture requires the implementation of both
manual and automatic key
management  (e.g., {{Section 4.5 of RFC4301}}).  Currently, the default automated key-management
protocol to implement is IKEv2. As required in {{RFC4301}}, IPv6
nodes implementing the IPsec Architecture MUST implement ESP {{RFC4303}} and MAY implement AH {{RFC4302}}.


## Transforms and Algorithms

The current set of mandatory-to-implement algorithms for the
IPsec Architecture are defined in Cryptographic
Algorithm Implementation Requirements for ESP and AH {{RFC8221}}.  IPv6 nodes implementing the IPsec
Architecture MUST conform to the requirements in {{RFC8221}}.
Preferred cryptographic algorithms often change more
frequently than security protocols. Therefore, implementations
MUST allow for migration to new algorithms, as RFC 8221 is
replaced or updated in the future.

The current set of mandatory-to-implement algorithms for
IKEv2 are defined in Cryptographic Algorithm Implementation
Requirements for ESP and AH {{RFC8247}}.  IPv6 nodes
implementing IKEv2 MUST conform to the requirements in {{RFC8247}} and/or any future
updates or replacements to {{RFC8247}}.



# Router-Specific Functionality

This section defines general host considerations for IPv6 nodes
that act as routers.  Currently, this section does not discuss
detailed routing-specific requirements. For the case of typical home routers, {{RFC7084}} defines basic requirements for customer edge routers.

## IPv6 Router Alert Option - RFC 2711

The IPv6 Router Alert option {{RFC2711}} is
an optional IPv6 Hop-by-Hop Header that is used in conjunction
with some protocols (e.g., RSVP {{RFC2205}} or
Multicast Listener Discovery (MLDv2) {{RFC3810}}).  The Router Alert option will
need to be implemented whenever such protocols that mandate its
use are implemented.  See {{mld}}.


## Neighbor Discovery for IPv6 - RFC 4861

Sending Router Advertisements and processing Router
Solicitations MUST be supported.

Routers SHOULD support {{RFC9131}} to avoid packet lost.

{{Section 7 of RFC6275}} includes some mobility-specific
extensions to Neighbor Discovery.
Routers SHOULD implement
Sections 7.3 and 7.5, even if they do not implement home
agent functionality.


## Stateful Address Autoconfiguration (DHCPv6) - RFC 8415

A single DHCP server ({{RFC8415}} or {{RFC4862}}) can provide configuration information to
devices directly attached to a shared link, as well as to
devices located elsewhere within a site. Communication between
a client and a DHCP server located on different links requires
the use of DHCP relay agents on routers.

In simple deployments, consisting of a single router and
either a single LAN or multiple LANs attached to the single
router, together with a WAN connection, a DHCP server
embedded within the router is one common deployment scenario
(e.g., {{RFC7084}}). There is no need
for relay agents in such scenarios.

In more complex deployment scenarios, such as within enterprise or service provider networks, the use of DHCP requires some level of configuration, in order to configure relay agents, prefixes for delegation, DHCP servers, etc. In such environments, the DHCP server might even be run on a traditional server, rather than as part of a router.

Because of the wide range of deployment scenarios, support for DHCP server functionality on routers is optional.  However, routers targeted for deployment within more complex scenarios (as described above) SHOULD support relay agent functionality including support for support DHCPv6-PD as defined in [RFC3633](?).  Note that "Basic Requirements for IPv6 Customer Edge Routers" [RFC7084] requires implementation of a DHCPv6 server function in IPv6 Customer Edge (CE) routers.


## IPv6 Prefix Length Recommendation for Forwarding - BCP 198

Forwarding nodes MUST conform to BCP 198 {{RFC7608}};
thus, IPv6 implementations of nodes that may forward packets
MUST conform to the rules specified in {{Section 5.1 of RFC4632}}.



# Constrained Devices

The focus of this document is general IPv6 nodes. In this section, we briefly
discuss considerations for constrained devices.

In the case of constrained nodes,
with limited CPU, memory, bandwidth or power, support for certain IPv6 functionality
may need
to be considered due to those limitations.  While the requirements of this
document are
RECOMMENDED for all nodes, including constrained nodes, compromises may need
to be
made in certain cases.  Where such compromises are made, the interoperability
of devices
should be strongly considered, particularly where this may impact other nodes
on the same
link, e.g., only supporting MLDv1 will affect other nodes.

The IETF 6LowPAN (IPv6 over Low-Power Wireless Personal Area Network) WG
produced six RFCs, including a general
overview and problem statement {{RFC4919}} (the means by which IPv6 packets
are transmitted over IEEE 802.15.4 networks {{RFC4944}} and ND optimizations for that medium {{RFC6775}}).

IPv6 nodes that are battery powered SHOULD implement the recommendations
in {{RFC7772}}.


# IPv6 Node Management

Network management MAY be supported by IPv6 nodes.  However,
for IPv6 nodes that are embedded devices, network management may
be the only possible way of controlling these nodes.

Existing network management protocols include SNMP {{RFC3411}}, NETCONF {{RFC6241}}, and RESTCONF {{RFC8040}}.

## Management Information Base (MIB) Modules

The obsoleted status of
various IPv6-specific MIB modules is clarified in {{RFC8096}}.

The following two MIB modules SHOULD be supported by nodes that
support an SNMP agent.

### IP Forwarding Table MIB

The IP Forwarding Table MIB {{RFC4292}} SHOULD be supported by nodes that support an
SNMP agent.


### Management Information Base for the Internet Protocol (IP)

The IP MIB {{RFC4293}} SHOULD be supported by nodes
that support an SNMP agent.


### Interface MIB

The Interface MIB {{RFC2863}} SHOULD be supported by nodes that support
an SNMP agent.



## YANG Data Models

The following YANG data models SHOULD be supported by nodes that support
a
NETCONF or RESTCONF agent.

### IP Management YANG Model

The IP Management YANG Model {{RFC8344}} SHOULD be supported
by nodes that support NETCONF or RESTCONF.


### Interface Management YANG Model

The Interface Management YANG Model {{RFC8343}} SHOULD be supported
by nodes that support NETCONF or RESTCONF.




# Security Considerations

This document does not directly affect the security of the
Internet, beyond the security considerations associated with the
individual protocols.

Security is also discussed in {{sec}} above.


# IANA Considerations

This document has no IANA actions.


--- back

# Changes from RFC 8504

This section highlights the changes since RFC 8504.

1. Updated obsoleted RFCs including 3315 and 3736 (both to 8415) and 4941 to 8981. RFC 793 has been obsoleted by 9293 but the latter does not include the the robustness principle for which RFC 793 is cited in this document.

1. Added support for RFC 9131.

1. Type C host from RFC 4191 is went from a SHOULD to MUST.

1. Removed the Mobility Section.

1. Removed the SEND Section.

1. Added Support for discovery of translation prefixes Section.

# Changes from RFC 6434 to RFC 8504

There have been many editorial clarifications as well as
significant additions and updates. While this section highlights
some of the changes, readers should not rely on this section for a
comprehensive list of all changes.

1. Restructured sections.

1. Added 6LoWPAN to link layers as it has some deployment.

1. Removed the Downstream-on-Demand (DoD) IPv6 Profile as it hasn't been updated.

1. Updated MLDv2 support to a MUST since nodes are restricted if MLDv1 is used.

1. Required DNS RA options so SLAAC-only devices can get DNS; RFC 8106 is a
  MUST.

1. Required RFC 3646 DNS Options for DHCPv6 implementations.

1. Added RESTCONF and NETCONF as possible options to network management.

1. Added a section on constrained devices.

1. Added text on RFC 7934 to address availability to hosts (SHOULD).

1. Added text on RFC 7844 for anonymity profiles for DHCPv6 clients.

1. Added mDNS and DNS-SD as updated service discovery.

1. Added RFC 8028 as a SHOULD as a method for solving a multi-prefix network.

1. Added ECN RFC 3168 as a SHOULD.

1. Added reference to RFC 7123 for security over IPv4-only networks.

1. Removed Jumbograms (RFC 2675) as they aren't deployed.

1. Updated obsoleted RFCs to the new version of the RFC, including RFCs 2460,
  1981, 7321, and 4307.

1. Added RFC 7772 for power consumptions considerations.

1. Added why /64 boundaries for more detail --- RFC 7421.

1. Added a unique IPv6 prefix per host to support currently deployed IPv6 networks.

1. Clarified RFC 7066 was a snapshot for 3GPP.

1. Updated RFC 4191 as a MUST and the Type C Host as a SHOULD as they help solve
  multi-prefix problems.

1. Removed IPv6 over ATM since there aren't many deployments.

1. Added a note in Section 6.6 for Rule 5.5 from RFC 6724.

1. Added MUST for BCP 198 for forwarding IPv6 packets.

1. Added a reference to RFC 8064 for stable address creation.

1. Added text on the protection from excessive extension header options.

1. Added text on the dangers of 1280 MTU UDP, especially with regard to DNS
  traffic.

1. Added text to clarify RFC 8200 behavior for unrecognized extension headers
  or unrecognized ULPs.

1. Removed dated email addresses from design team acknowledgements for {{RFC4294}}.



# Changes from RFC 4294 to RFC 6434

There have been many editorial clarifications as well as
significant additions and updates. While this section highlights
some of the changes, readers should not rely on this section for a
comprehensive list of all changes.



1. Updated the Introduction to indicate that this document is an
  applicability statement and is aimed at
  general nodes.

1. Significantly updated the section on mobility protocols;
  added references and downgraded previous SHOULDs to MAYs.

1. Changed the Sub-IP Layer section to just list relevant RFCs, and
  added some more RFCs.

1. Added a section on SEND (it is a MAY).

1. Revised the section on Privacy Extensions to add more
  nuance to the recommendation.

1. Completely revised the IPsec/IKEv2 section, downgrading the overall
  recommendation to a SHOULD.

1. Upgraded recommendation of DHCPv6 to a SHOULD.

1. Added a background section on DHCP versus RA options, added
  a SHOULD recommendation for DNS configuration via RAs (RFC 6106), and cleaned
  up the DHCP recommendations.

1. Added the recommendation that routers implement Sections 7.3 and
  7.5 of {{RFC6275}}.

1. Added a pointer to subnet clarification document {{RFC5942}}.

1. Added text that "IPv6 Host-to-Router Load Sharing" {{RFC4311}} SHOULD be implemented.

1. Added reference to {{RFC5722}} (Overlapping Fragments),
  and made it a MUST to implement.

1. Made "A Recommendation for IPv6 Address Text Representation" {{RFC5952}} a SHOULD.

1. Removed the mention of delegation name (DNAME) from the discussion about {{RFC3363}}.

1. Numerous updates to reflect newer versions of IPv6
  documents, including {{RFC3596}}, {{RFC4213}}, {{RFC4291}}, and {{RFC4443}}.

1. Removed discussion of "Managed" and "Other" flags in
  RAs. There is no consensus at present on how to process these
  flags, and discussion of their semantics was removed in the most
  recent update of Stateless Address Autoconfiguration {{RFC4862}}.

1. Added many more references to optional IPv6 documents.

1. Made "A Recommendation for IPv6 Address Text Representation" {{RFC5952}} a SHOULD.

1. Updated the MLD section to include reference to Lightweight MLD {{RFC5790}}.

1. Added a SHOULD recommendation for "Default Router Preferences
  and More-Specific Routes" {{RFC4191}}.

1. Made "IPv6 Flow Label Specification" {{RFC6437}} a SHOULD.


# Acknowledgments
{:numbered="no"}

* Acknowledgements from (Current Documents)

  The authors would like to thank Nick Buraglio, Brian Carpenter, and Jeremy Duncan
  for their contributions and many members of the 6man WG for the inputs they gave.

* Acknowledgments from RFC 8504

  The authors would like to thank
  Brian Carpenter, Dave Thaler,
  Tom Herbert, Erik Kline, Mohamed Boucadair, and Michayla Newcombe
  for their contributions and many members of the 6man WG for the inputs they
  gave.

* Authors and Acknowledgments from RFC 6434

  RFC 6434 was authored by Ed Jankiewicz, John Loughney, and Thomas Narten.

  The authors of RFC 6434 thank Hitoshi Asaeda, Brian Carpenter, Tim Chown,
  Ralph
  Droms, Sheila Frankel, Sam Hartman, Bob Hinden, Paul Hoffman, Pekka
  Savola, Yaron Sheffer, and Dave Thaler for their comments.  In addition,
  the authors thank Mark Andrews for comments and corrections on DNS
  text and Alfred Hoenes for tracking the updates to various RFCs.

* Authors and Acknowledgments from RFC 4294

  RFC 4294 was written by
  the IPv6 Node Requirements design team, which had the following members:
  Jari Arkko,
  Marc Blanchet,
  Samita Chakrabarti,
  Alain Durand,
  Gerard Gastaud,
  Jun-ichiro Itojun Hagino,
  Atsushi Inoue,
  Masahiro Ishiyama,
  John Loughney,
  Rajiv Raghunarayan,
  Shoichi Sakane,
  Dave Thaler, and Juha Wiljakka.

  The authors of RFC 4294 thank Ran Atkinson, Jim Bound, Brian Carpenter, Ralph
  Droms,
  Christian Huitema, Adam Machalek, Thomas Narten, Juha Ollila, and Pekka
  Savola for their comments.


