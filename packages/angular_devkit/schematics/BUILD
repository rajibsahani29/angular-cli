# Copyright Google Inc. All Rights Reserved.
#
# Use of this source code is governed by an MIT-style license that can be
# found in the LICENSE file at https://angular.io/license
package(default_visibility = ["//visibility:public"])

load("@build_bazel_rules_typescript//:defs.bzl", "ts_library")
load("@build_bazel_rules_nodejs//:defs.bzl", "jasmine_node_test")

licenses(["notice"])  # MIT License

# @angular-devkit/schematics

ts_library(
    name = "schematics",
    srcs = glob(
        include = ["src/**/*.ts"],
        exclude = [
            "src/**/*_spec.ts",
            "src/**/*_spec_large.ts",
            "src/**/*_benchmark.ts",
        ],
    ),
    module_name = "@angular-devkit/schematics",
    module_root = "src/index.d.ts",
    deps = [
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",  # TODO: get rid of this for 6.0
        "@rxjs",
        "@rxjs//operators",
        # @typings: node
    ],
)

ts_library(
    name = "schematics_test_lib",
    srcs = glob(
        include = [
            "src/**/*_spec.ts",
            "src/**/*_spec_large.ts",
        ],
    ),
    deps = [
        ":schematics",
        ":testing",
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",
        "@rxjs",
        "@rxjs//operators",
        # @typings: jasmine
        # @typings: node
    ],
)

jasmine_node_test(
    name = "schematics_test",
    srcs = [":schematics_test_lib"],
)


# @angular-devkit/schematics/tasks

ts_library(
    name = "tasks",
    srcs = glob(
        include = ["tasks/**/*.ts"],
        exclude = [
            "tasks/**/*_spec.ts",
            "tasks/**/*_benchmark.ts",
            "tasks/tslint-fix/test/**/*",
        ],
    ),
    module_name = "@angular-devkit/schematics/tasks",
    module_root = "tasks/index.d.ts",
    deps = [
        ":schematics",
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",
        "@rxjs",
        "@rxjs//operators",
        # @typings: node
        # @typings: tslint
        # @typings: typescript
    ],
)

ts_library(
    name = "tasks_test_lib",
    srcs = glob(
        include = [
            "tasks/**/*_spec.ts",
            "tasks/**/*_spec_large.ts",
            "tasks/tslint-fix/test/**/*.ts",
        ],
    ),
    data = [
        "tasks/tslint-fix/test/collection.json",
        "tasks/tslint-fix/test/rules/customRuleRule.js",
    ],
    deps = [
        ":tasks",
        ":testing",
        ":schematics",
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",
        "//packages/angular_devkit/core:node_testing",
        "@rxjs",
        "@rxjs//operators",
        # @typings: jasmine
        # @typings: node
    ],
)


jasmine_node_test(
    name = "tasks_test",
    srcs = [":tasks_test_lib"],
)


# @angular-devkit/schematics/tools

ts_library(
    name = "tools",
    srcs = glob(
        include = ["tools/**/*.ts"],
        exclude = [
            "tools/**/*_spec.ts",
            "tools/**/*_benchmark.ts",
            "tools/test/**/*.ts",
        ],
    ),
    module_name = "@angular-devkit/schematics/tools",
    module_root = "tools/index.d.ts",
    deps = [
        ":schematics",
        ":tasks",
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",
        "@rxjs",
        "@rxjs//operators",
        # @typings: node
    ],
)

ts_library(
    name = "tools_test_lib",
    srcs = glob(
        include = [
            "tools/**/*_spec.ts",
            "tools/**/*_spec_large.ts",
            "tools/test/**/*.ts",
        ],
    ),
    deps = [
        ":tools",
        ":tasks",
        ":schematics",
        ":testing",
        "//packages/angular_devkit/core",
        "//packages/angular_devkit/core:node",
        "//tests/angular_devkit/schematics/tools/file-system-engine-host:file_system_engine_host_test_lib",
        "@rxjs",
        "@rxjs//operators",
        # @typings: jasmine
        # @typings: node
    ],
)

jasmine_node_test(
    name = "tools_test",
    srcs = [":tools_test_lib"],
)


# @angular-devkit/schematics/testing

ts_library(
    name = "testing",
    srcs = glob(
        include = ["testing/**/*.ts"],
    ),
    module_name = "@angular-devkit/schematics/testing",
    module_root = "testing/index.d.ts",
    deps = [
        ":schematics",
        ":tasks",
        ":tools",
        "//packages/angular_devkit/core",
        "@rxjs",
        "@rxjs//operators",
    ],
)