### Heap Dump

You can use the Steeltoe heap dump endpoint to generate and download a mini-dump of your application. The mini-dump can then be read into Visual Studio for analysis.

>NOTE: At this time, dumps are possible only on the Windows operating system. When integrating with the [Pivotal Apps Manager](https://docs.pivotal.io/pivotalcf/2-0/console/index.html), you do not have the ability to obtain dumps from applications running on Linux cells. Also, the heap dump filename used by the Pivotal Apps Manager ends with the `.hprof` extension instead of the usual `.dmp` extension. This may cause problems when opening the dump with Visual Studio or some other diagnostic tool. As a workaround, you can rename the file to use the `.dmp` extension.

#### Configure Settings

The following table describes the settings that you can apply to the endpoint:

|Key|Description|Default|
|---|---|---|
|`Id`|The ID of the heap dump endpoint|`heapdump`|
|`Enabled`|Whether to enable the heap dump management endpoint|`true`|
|`Sensitive`|Currently not used|`false`|

>NOTE: Each setting above must be prefixed with `Management:Endpoints:Heapdump`.

#### Enable HTTP Access

The default path to the heap dump endpoint is computed by combining the global `Path` prefix setting together with the `Id` setting described in the previous section. The default path is `/heapdump`.

To add the heap dump actuator to the service container, use the `AddHeapDumpActuator()` extension method from `EndpointServiceCollectionExtensions`.

To add the heap dump actuator middleware to the ASP.NET Core pipeline, use the `UseHeapDumpActuator()` extension method from `EndpointApplicationBuilderExtensions`.