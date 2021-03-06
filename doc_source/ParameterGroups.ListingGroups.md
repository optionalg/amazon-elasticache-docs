# Listing Parameter Groups by Name<a name="ParameterGroups.ListingGroups"></a>

You can list the parameter groups using the ElastiCache console, the AWS CLI, or the ElastiCache API\.

## Listing Parameter Groups by Name \(Console\)<a name="ParameterGroups.ListingGroups.CON"></a>

The following procedure shows how to view a list of the parameter groups using the ElastiCache console\.

**To list parameter groups using the ElastiCache console**

1. Sign in to the AWS Management Console and open the ElastiCache console at [ https://console\.aws\.amazon\.com/elasticache/](https://console.aws.amazon.com/elasticache/)\.

1. To see a list of all available parameter groups, in the left hand navigation pane choose **Parameter Groups**\.

## Listing Parameter Groups by Name \(AWS CLI\)<a name="ParameterGroups.ListingGroups.CLI"></a>

To generate a list of parameter groups using the AWS CLI, use the command `describe-cache-parameter-groups`\. If you provide a parameter group's name, only that parameter group will be listed\. If you do not provide a parameter group's name, up to `--max-records` parameter groups will be listed\. In either case, the parameter group's name, family, and description are listed\.

The following sample code lists the parameter group *myRedis28*\.

For Linux, macOS, or Unix:

```
aws elasticache describe-cache-parameter-groups \
    --cache-parameter-group-name myredis28
```

For Windows:

```
aws elasticache describe-cache-parameter-groups ^
    --cache-parameter-group-name myredis28
```

The output of this command will look something like this, listing the name, family, and description for the parameter group\.

```
{
    "CacheParameterGroups": [
	    {
	        "CacheParameterGroupName": "myredis28", 
	        "CacheParameterGroupFamily": "redis2.8", 
	        "Description": "My first  parameter group"
	    }
    ]
}
```

The following sample code lists up to 10 parameter groups\.

```
aws elasticache describe-cache-parameter-groups --max-records 20
```

The JSON output of this command will look something like this, listing the name, family, and description for each parameter group\.

```
{
    "CacheParameterGroups": [
        {
            "CacheParameterGroupName": "custom-redis32", 
            "CacheParameterGroupFamily": "redis3.2", 
            "Description": "custom parameter group with reserved-memory > 0"
        }, 
        {
            "CacheParameterGroupName": "default.memcached1.4", 
            "CacheParameterGroupFamily": "memcached1.4", 
            "Description": "Default parameter group for memcached1.4"
        }, 
        {
            "CacheParameterGroupName": "default.redis2.6", 
            "CacheParameterGroupFamily": "redis2.6", 
            "Description": "Default parameter group for redis2.6"
        }, 
        {
            "CacheParameterGroupName": "default.redis2.8", 
            "CacheParameterGroupFamily": "redis2.8", 
            "Description": "Default parameter group for redis2.8"
        }, 
        {
            "CacheParameterGroupName": "default.redis3.2", 
            "CacheParameterGroupFamily": "redis3.2", 
            "Description": "Default parameter group for redis3.2"
        }, 
        {
            "CacheParameterGroupName": "default.redis3.2.cluster.on", 
            "CacheParameterGroupFamily": "redis3.2", 
            "Description": "Customized default parameter group for redis3.2 with cluster mode on"
        }
    ]
}
```

For more information, see [http://docs.aws.amazon.com/cli/latest/reference/elasticache/describe-cache-parameter-groups.html](http://docs.aws.amazon.com/cli/latest/reference/elasticache/describe-cache-parameter-groups.html)\.

## Listing Parameter Groups by Name \(ElastiCache API\)<a name="ParameterGroups.ListingGroups.API"></a>

To generate a list of parameter groups using the ElastiCache API, use the `DescribeCacheParameterGroups` action\. If you provide a parameter group's name, only that parameter group will be listed\. If you do not provide a parameter group's name, up to `MaxRecords` parameter groups will be listed\. In either case, the parameter group's name, family, and description are listed\.

The following sample code lists the parameter group *myRedis28*\.

```
https://elasticache.us-west-2.amazonaws.com/
   ?Action=DescribeCacheParameterGroups
   &CacheParameterGroupName=myRedis28
   &SignatureVersion=4
   &SignatureMethod=HmacSHA256
   &Timestamp=20150202T192317Z
   &Version=2015-02-02
   &X-Amz-Credential=<credential>
```

The response from this action will look something like this, listing the name, family, and description for each parameter group\.

```
<DescribeCacheParameterGroupsResponse xmlns="http://elasticache.amazonaws.com/doc/2013-06-15/">
  <DescribeCacheParameterGroupsResult>
    <CacheParameterGroups>
      <CacheParameterGroup>
        <CacheParameterGroupName>myRedis28</CacheParameterGroupName>
        <CacheParameterGroupFamily>redis 2.8</CacheParameterGroupFamily>
        <Description>My Redis 2.8 parameter group</Description>
      </CacheParameterGroup>
    </CacheParameterGroups>
  </DescribeCacheParameterGroupsResult>
  <ResponseMetadata>
    <RequestId>3540cc3d-af48-11e0-97f9-279771c4477e</RequestId>
  </ResponseMetadata>
</DescribeCacheParameterGroupsResponse>
```

The following sample code lists up to 10 parameter groups\.

```
https://elasticache.us-west-2.amazonaws.com/
   ?Action=DescribeCacheParameterGroups
   &MaxRecords=10
   &SignatureVersion=4
   &SignatureMethod=HmacSHA256
   &Timestamp=20150202T192317Z
   &Version=2015-02-02
   &X-Amz-Credential=<credential>
```

The response from this action will look something like this, listing the name, family, and description for each parameter group\.

```
<DescribeCacheParameterGroupsResponse xmlns="http://elasticache.amazonaws.com/doc/2013-06-15/">
  <DescribeCacheParameterGroupsResult>
    <CacheParameterGroups>
      <CacheParameterGroup>
        <CacheParameterGroupName>myRedis28</CacheParameterGroupName>
        <CacheParameterGroupFamily>redis2.8</CacheParameterGroupFamily>
        <Description>My Redis 2.8 parameter group</Description>
      </CacheParameterGroup>
      <CacheParameterGroup>
        <CacheParameterGroupName>myMem14</CacheParameterGroupName>
        <CacheParameterGroupFamily>memcached1.4</CacheParameterGroupFamily>
        <Description>My Memcached 1.4 parameter group</Description>
      </CacheParameterGroup>
    </CacheParameterGroups>
  </DescribeCacheParameterGroupsResult>
  <ResponseMetadata>
    <RequestId>3540cc3d-af48-11e0-97f9-279771c4477e</RequestId>
  </ResponseMetadata>
</DescribeCacheParameterGroupsResponse>
```

For more information, see [http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameterGroups.html](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameterGroups.html)\.