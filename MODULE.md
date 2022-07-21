<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.0 |
| <a name="requirement_kubernetes"></a> [kubernetes](#requirement\_kubernetes) | >= 2.4.1 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_kubernetes"></a> [kubernetes](#provider\_kubernetes) | >= 2.4.1 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [kubernetes_cluster_role.this](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/cluster_role) | resource |
| [kubernetes_cluster_role_binding.this](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/cluster_role_binding) | resource |
| [kubernetes_daemonset.this](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/daemonset) | resource |
| [kubernetes_service_account.this](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/service_account) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cordon_only"></a> [cordon\_only](#input\_cordon\_only) | If true, nodes will be cordoned but not drained when an interruption event occurs. | `bool` | `false` | no |
| <a name="input_delete_local_data"></a> [delete\_local\_data](#input\_delete\_local\_data) | If true, do not drain pods that are using local node storage in emptyDir. | `bool` | `true` | no |
| <a name="input_enable_prometheus_server"></a> [enable\_prometheus\_server](#input\_enable\_prometheus\_server) | Whether to enable a Prometheus endpoint that can be used to gather some metrics. | `bool` | `false` | no |
| <a name="input_enable_scheduled_event_draining"></a> [enable\_scheduled\_event\_draining](#input\_enable\_scheduled\_event\_draining) | If true, drain nodes before the maintenance window starts for an EC2 instance scheduled event. | `bool` | `false` | no |
| <a name="input_enable_spot_interruption_draining"></a> [enable\_spot\_interruption\_draining](#input\_enable\_spot\_interruption\_draining) | If true, drain nodes when the spot interruption termination notice is received. | `bool` | `true` | no |
| <a name="input_ignore_daemon_sets"></a> [ignore\_daemon\_sets](#input\_ignore\_daemon\_sets) | If true, ignore daemon sets and drain other pods when a spot interrupt is received. | `bool` | `true` | no |
| <a name="input_json_logging"></a> [json\_logging](#input\_json\_logging) | If true, use JSON-formatted logs instead of human readable logs. | `bool` | `false` | no |
| <a name="input_k8s_node_selector"></a> [k8s\_node\_selector](#input\_k8s\_node\_selector) | Node selector to make sure that the node termination handler only runs on spot instances. | `map(string)` | <pre>{<br>  "lifecycle": "Ec2Spot"<br>}</pre> | no |
| <a name="input_k8s_node_tolerations"></a> [k8s\_node\_tolerations](#input\_k8s\_node\_tolerations) | Additional tolerations required to run on spot instances within the cluster. | <pre>list(object({<br>    effect   = string<br>    key      = string<br>    operator = string<br>    value    = string<br>  }))</pre> | <pre>[<br>  {<br>    "effect": "NoSchedule",<br>    "key": "lifecycle",<br>    "operator": "Equal",<br>    "value": "Ec2Spot"<br>  }<br>]</pre> | no |
| <a name="input_k8s_pod_annotations"></a> [k8s\_pod\_annotations](#input\_k8s\_pod\_annotations) | Additional annotations to be added to the Pods. | `map(string)` | `{}` | no |
| <a name="input_metadata_tries"></a> [metadata\_tries](#input\_metadata\_tries) | The number of times to try requesting metadata. If you would like 2 retries, set metadata-tries to 3. | `number` | `3` | no |
| <a name="input_node_termination_grace_period"></a> [node\_termination\_grace\_period](#input\_node\_termination\_grace\_period) | Period of time in seconds given to each NODE to terminate gracefully. Node draining will be scheduled based on this value to optimize the amount of compute time, but still safely drain the node before an event. | `string` | `"120"` | no |
| <a name="input_node_termination_handler_version"></a> [node\_termination\_handler\_version](#input\_node\_termination\_handler\_version) | The version to use. See https://github.com/aws/aws-node-termination-handler/releases for available versions | `string` | `"1.13.3"` | no |
| <a name="input_pod_termination_grace_period"></a> [pod\_termination\_grace\_period](#input\_pod\_termination\_grace\_period) | Period of time in seconds given to each POD to terminate gracefully. If negative, the default value specified in the pod will be used. | `string` | `"-1"` | no |
| <a name="input_taint_node"></a> [taint\_node](#input\_taint\_node) | If true, nodes will be tainted when an interruption event occurs. | `bool` | `false` | no |
| <a name="input_webhook_headers"></a> [webhook\_headers](#input\_webhook\_headers) | If specified, replaces the default webhook headers. | `map(string)` | <pre>{<br>  "Content-type": "application/json"<br>}</pre> | no |
| <a name="input_webhook_proxy"></a> [webhook\_proxy](#input\_webhook\_proxy) | If specified, uses the HTTP(S) proxy to send webhooks. | `string` | `""` | no |
| <a name="input_webhook_template"></a> [webhook\_template](#input\_webhook\_template) | If specified, replaces the default webhook message template. | `string` | `""` | no |
| <a name="input_webhook_url"></a> [webhook\_url](#input\_webhook\_url) | If specified, posts event data to URL upon instance interruption action. | `string` | `""` | no |

## Outputs

No outputs.
<!-- END_TF_DOCS -->